```vue
<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

// Data dummy berita

const heroNews = ref([
  {
    id: 1,
    title: 'Masjid Menjadi Pusat Kegiatan Keislaman dan Pemberdayaan Umat',
    author: 'Berita Terbaru',
    date: '19 Agustus 2026',
    image: 'https://picsum.photos/seed/masjid1/1200/700',
  },
  {
    id: 2,
    title: 'Pentingnya Membiasakan Membaca Al-Qur’an Setiap Hari',
    author: 'Berita Terbaru',
    date: '18 Agustus 2026',
    image: 'https://picsum.photos/seed/quran1/1200/700',
  },
  {
    id: 3,
    title: 'Kajian Islam Bahas Pentingnya Menjaga Silaturahmi di Tengah Kesibukan',
    author: 'Berita Terbaru',
    date: '17 Agustus 2026',
    image: 'https://picsum.photos/seed/islam1/1200/700',
  },
])

const otherNews = ref([
  {
    id: 4,
    title: 'Masjid Gelar Kajian Rutin Setiap Pekan',
    date: '19 Agu 2026',
    image: 'https://picsum.photos/seed/kajian1/200/200',
  },
  {
    id: 5,
    title: 'Gerakan Sedekah Berbagi untuk Masyarakat Sekitar Masjid',
    date: '18 Agu 2026',
    image: 'https://picsum.photos/seed/sedekah1/200/200',
  },
  {
    id: 6,
    title: 'Anak-Anak Ikuti Program Belajar Al-Qur’an di Masjid',
    date: '18 Agu 2026',
    image: 'https://picsum.photos/seed/ngaji1/200/200',
  },
  {
    id: 7,
    title: 'Remaja Masjid Gelar Kegiatan Sosial untuk Warga',
    date: '17 Agu 2026',
    image: 'https://picsum.photos/seed/remaja1/200/200',
  },
  {
    id: 8,
    title: 'Keutamaan Shalat Berjamaah dan Memakmurkan Masjid',
    date: '16 Agu 2026',
    image: 'https://picsum.photos/seed/sholat1/200/200',
  },
])

const newsCards = ref([
  {
    id: 9,
    title: 'Remaja Masjid Berperan Penting dalam Membangun Generasi Islami',
    author: 'masjidKu',
    date: '19 Agu 2026',
    excerpt:
      'Kegiatan positif remaja masjid menjadi salah satu cara untuk membangun generasi muda yang aktif, peduli, dan dekat dengan nilai-nilai Islam.',
    image: 'https://picsum.photos/seed/remaja2/600/400',
  },
  {
    id: 10,
    title: 'Sedekah dan Berbagi Menjadi Wujud Kepedulian terhadap Sesama',
    author: 'masjidKu',
    date: '18 Agu 2026',
    excerpt:
      'Berbagi kepada sesama tidak hanya membantu mereka yang membutuhkan, tetapi juga menjadi salah satu bentuk kepedulian dan amal dalam kehidupan sehari-hari.',
    image: 'https://picsum.photos/seed/sedekah2/600/400',
  },
  {
    id: 11,
    title: 'Mengajarkan Al-Qur’an Sejak Dini untuk Membentuk Generasi Qurani',
    author: 'masjidKu',
    date: '18 Agu 2026',
    excerpt:
      'Pembelajaran Al-Qur’an sejak usia dini dapat menjadi fondasi penting dalam membentuk karakter dan kecintaan anak terhadap ajaran Islam.',
    image: 'https://picsum.photos/seed/quran2/600/400',
  },
])

// =========================
// CAROUSEL
// =========================

const currentSlide = ref(0)
let autoplayTimer = null

// Fungsi untuk mengubah slide berikutnya, sebelumnya, dan langsung ke slide tertentu
function nextSlide() {
  currentSlide.value = (currentSlide.value + 1) % heroNews.value.length
}

function prevSlide() {
  currentSlide.value = (currentSlide.value - 1 + heroNews.value.length) % heroNews.value.length
}

function goToSlide(index) {
  currentSlide.value = index
}

function startAutoplay() {
  stopAutoplay()

  autoplayTimer = setInterval(() => {
    nextSlide()
  }, 5000)
}

function stopAutoplay() {
  if (autoplayTimer) {
    clearInterval(autoplayTimer)
    autoplayTimer = null
  }
}

onMounted(() => {
  startAutoplay()
})

onUnmounted(() => {
  stopAutoplay()
})
</script>

<template>
  <div class="container max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
    <!-- SECTION TITLE -->
    <h1 class="text-3xl uppercase text-center font-bold text-cyan-700 mb-8">Berita Terkini</h1>

    <!-- HERO NEWS + OTHER NEWS -->
    <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
      <!-- HERO CAROUSEL -->
      <div
        class="lg:col-span-2 relative rounded-2xl overflow-hidden aspect-4/3 sm:aspect-video group"
        @mouseenter="stopAutoplay"
        @mouseleave="startAutoplay"
      >
        <!-- SLIDES -->
        <div
          class="flex h-full transition-transform duration-700 ease-out"
          :style="{
            transform: `translateX(-${currentSlide * 100}%)`,
          }"
        >
          <div
            v-for="slide in heroNews"
            :key="slide.id"
            class="relative w-full h-full shrink-0"
          >
            <!-- IMAGE -->
            <img :src="slide.image" loading="lazy" :alt="slide.title" class="w-full h-full object-cover" />

            <!-- OVERLAY -->
            <div
              class="absolute inset-0 bg-linear-to-t from-black/80 via-black/20 to-transparent"
            ></div>

            <!-- TEXT -->
            <div class="absolute bottom-0 left-0 right-0 p-5 sm:p-8">
              <span
                class="inline-block bg-cyan-700 text-white text-xs font-semibold px-3 py-1 rounded-full mb-3"
              >
                {{ slide.author }}
              </span>

              <h2
                class="text-white text-xl sm:text-2xl lg:text-3xl font-bold leading-tight mb-2 max-w-2xl"
              >
                {{ slide.title }}
              </h2>

              <p class="text-gray-200 text-sm">
                {{ slide.date }}
              </p>
            </div>
          </div>
        </div>

        <!-- PREVIOUS BUTTON -->
        <button
          type="button"
          @click="prevSlide"
          class="absolute left-3 cursor-pointer top-1/2 -translate-y-1/2 bg-white/20 hover:bg-white/40 backdrop-blur-sm text-white rounded-full w-9 h-9 flex items-center justify-center opacity-0 group-hover:opacity-100 transition-opacity"
          aria-label="Sebelumnya"
        >
          ‹
        </button>

        <!-- NEXT BUTTON -->
        <button
          type="button"
          @click="nextSlide"
          class="absolute right-3 cursor-pointer top-1/2 -translate-y-1/2 bg-white/20 hover:bg-white/40 backdrop-blur-sm text-white rounded-full w-9 h-9 flex items-center justify-center opacity-0 group-hover:opacity-100 transition-opacity"
          aria-label="Berikutnya"
        >
          ›
        </button>

        <!-- DOTS -->
        <div class="absolute bottom-3 right-5 flex gap-2">
          <button
            v-for="(slide, index) in heroNews"
            :key="slide.id"
            type="button"
            @click="goToSlide(index)"
            class="h-2 rounded-full transition-all"
            :class="index === currentSlide ? 'w-6 bg-white' : 'w-2 bg-white/50'"
            :aria-label="`Slide ${index + 1}`"
          ></button>
        </div>
      </div>

      <!-- BERITA LAINNYA -->
      <div class="flex flex-col divide-y divide-gray-100 rounded-2xl border border-gray-100 p-4">
        <h3 class="text-sm font-semibold text-gray-500 uppercase tracking-wide pb-3">
          Berita Lainnya
        </h3>

        <a
          v-for="item in otherNews"
          :key="item.id"
          href="#"
          class="flex gap-3 py-3 group first:pt-3"
        >
          <!-- IMAGE -->
          <img
            :src="item.image"
            :alt="item.title"
            loading="lazy"
            class="w-16 h-16 rounded-lg object-cover shrink-0"
          />

          <!-- CONTENT -->
          <div class="min-w-0">
            <p
              class="text-sm font-medium text-gray-900 line-clamp-2 group-hover:text-indigo-600 transition-colors"
            >
              {{ item.title }}
            </p>

            <p class="text-xs text-gray-400 mt-1">
              {{ item.date }}
            </p>
          </div>
        </a>
      </div>
    </div>

    <!-- NEWS CARDS -->
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6 mt-8">
      <a
        v-for="card in newsCards"
        :key="card.id"
        href="#"
        class="group rounded-2xl overflow-hidden border border-gray-100 hover:shadow-lg transition-shadow"
      >
        <!-- IMAGE -->
        <div class="aspect-16/10 overflow-hidden">
          <img
            :src="card.image"
            loading="lazy"
            :alt="card.title"
            class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500"
          />
        </div>

        <!-- CONTENT -->
        <div class="p-5">
          <!-- CATEGORY + DATE -->
          <div class="flex items-center gap-2 mb-2">
            <span class="text-xs font-semibold text-indigo-600">
              {{ card.author }}
            </span>

            <span class="text-xs text-gray-300"> • </span>

            <span class="text-xs text-gray-400">
              {{ card.date }}
            </span>
          </div>

          <!-- TITLE -->
          <h3
            class="font-bold text-gray-900 mb-2 line-clamp-2 group-hover:text-indigo-600 transition-colors"
          >
            {{ card.title }}
          </h3>

          <!-- EXCERPT -->
          <p class="text-sm text-gray-500 line-clamp-2">
            {{ card.excerpt }}
          </p>
        </div>
      </a>
    </div>
  </div>
</template>
```
