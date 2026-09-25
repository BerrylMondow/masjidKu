<script setup>
import { ref, computed, onMounted, onUnmounted } from 'vue'

// Data dummy — nanti diganti hasil fetch dari API jadwal sholat
const jadwalSholat = ref([
  { name: 'Shubuh', time: '04:12' },
  { name: 'Syuruq', time: '05:38' },
  { name: 'Dzuhur', time: '11:35' },
  { name: 'Ashar', time: '14:52' },
  { name: 'Maghrib', time: '17:41' },
  { name: 'Isya', time: '18:53' },
  { name: 'Imsak', time: '04:02' },
])

// Buat variabel waktu saat ini
const now = ref(new Date())
let timer = null

// Memperbarui waktu secara real-time
onMounted(() => {
  timer = setInterval(() => {
    now.value = new Date()
  }, 1000)
})

// Hentikan timer ketika komponen dilepas
onUnmounted(() => {
  if (timer) clearInterval(timer)
})

// Menampilkan waktu saat ini
const currentTimeLabel = computed(() =>
  now.value.toLocaleTimeString('id-ID', { hour: '2-digit', minute: '2-digit', second: '2-digit' }),
)

// Menampilkan tanggal hari ini
const todayLabel = computed(() =>
  now.value.toLocaleDateString('id-ID', {
    weekday: 'long',
    day: 'numeric',
    month: 'long',
    year: 'numeric',
  }),
)

// Ubah "HH:mm" jadi Date hari ini
function toTodayDate(timeStr) {
  const [h, m] = timeStr.split(':').map(Number)
  const d = new Date(now.value)
  d.setHours(h, m, 0, 0)
  return d
}

// Urutan sholat wajib untuk countdown (Imsak dikecualikan dari perhitungan "next prayer" utama,
// tapi tetap tampil di tabel)
const urutanSholat = computed(() => jadwalSholat.value.filter((j) => j.name !== 'Imsak'))

// Menentukan waktu sholat berikutnya
const nextPrayer = computed(() => {
  const list = urutanSholat.value
  for (const j of list) {
    if (toTodayDate(j.time).getTime() > now.value.getTime()) {
      // Mengembalikan sholat berikutnya
      return { name: j.name, target: toTodayDate(j.time) }
    }
  }
  const shubuh = list.find((j) => j.name === 'Shubuh')
  const target = toTodayDate(shubuh.time)

  // Jika sudah lewat semua jadwal sholat hari ini, kembali ke Shubuh pada hari berikutnya
  target.setDate(target.getDate() + 1)
  return { name: shubuh.name, target }
})

// Waktu sholat yang sedang "aktif" (sudah lewat, jadi disorot di tabel sebagai waktu terakhir berlaku)
const activePrayer = computed(() => {
  // Mengambil daftar sholat
  const list = urutanSholat.value
  let active = null

  // Memeriksa setiap waktu sholat
  for (const j of list) {
    // Membandingkan waktu sholat dengan waktu sekarang
    if (toTodayDate(j.time).getTime() <= now.value.getTime()) {
      active = j
    }
  }
  return active
})

// Countdown ke sholat berikutnya
const countdownLabel = computed(() => {
  // Menghitung selisih waktu dalam milidetik
  const diff = nextPrayer.value.target.getTime() - now.value.getTime()
  // Mengubah selisih waktu menjadi format HH:mm:ss
  const totalSec = Math.max(0, Math.floor(diff / 1000))
  const h = String(Math.floor(totalSec / 3600)).padStart(2, '0')
  const m = String(Math.floor((totalSec % 3600) / 60)).padStart(2, '0')
  const s = String(totalSec % 60).padStart(2, '0')
  return `${h}:${m}:${s}`
})
</script>

<template>
  <div
    class="bg-white/5 backdrop-blur-md border border-white/10 rounded-3xl p-6 sm:p-8 w-full lg:max-w-lg lg:ml-auto"
  >
    <div class="flex items-center justify-between mb-6">
      <div>
        <h2 class="text-2xl font-bold text-gray-100">Jadwal Sholat</h2>
        <p class="text-gray-400 text-sm">{{ todayLabel }}</p>
      </div>
      <div class="text-right">
        <p class="text-gray-400 text-xs">Waktu Sekarang</p>
        <p class="text-gray-100 text-xl font-semibold tabular-nums">
          {{ currentTimeLabel }}
        </p>
      </div>
    </div>

    <!-- Countdown ke sholat berikutnya -->
    <div
      class="bg-linear-to-r from-cyan-600/20 to-green-600/20 border border-cyan-500/30 rounded-2xl p-5 mb-6 flex items-center justify-between flex-wrap gap-3"
    >
      <div>
        <p class="text-gray-300 text-sm">Menuju waktu</p>
        <p class="text-cyan-400 text-2xl font-bold">{{ nextPrayer.name }}</p>
      </div>
      <div class="text-right">
        <p class="text-gray-300 text-sm">Countdown</p>
        <p class="text-gray-100 text-3xl font-mono font-bold tabular-nums">
          {{ countdownLabel }}
        </p>
      </div>
    </div>

    <!-- Tabel waktu sholat -->
    <div class="grid grid-cols-3 sm:grid-cols-6 lg:grid-cols-3 gap-3">
      <div
        v-for="jadwal in jadwalSholat"
        :key="jadwal.name"
        class="rounded-xl p-4 text-center border transition-colors duration-200"
        :class="
          jadwal.name === activePrayer?.name
            ? 'bg-cyan-500/20 border-cyan-500 text-cyan-300'
            : 'bg-white/5 border-white/10 text-gray-300'
        "
      >
        <p class="text-xs uppercase tracking-wide mb-1">{{ jadwal.name }}</p>
        <p class="text-lg font-semibold tabular-nums">{{ jadwal.time }}</p>
      </div>
    </div>
  </div>
</template>
