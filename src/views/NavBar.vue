<script setup>
import { ref, onMounted, onUnmounted, watch } from 'vue'
import { useRoute } from 'vue-router'

const route = useRoute()

const isOpen = ref(false)
const navbarOpacity = ref(0)

const menuItems = [
  { name: 'Beranda', href: '/' },
  { name: 'Tentang Kami', href: '/about' },
  { name: 'Berita', href: '#' },
  { name: 'Donasi', href: '#' },
]

const handleScroll = () => {
  // Halaman selain homepage selalu putih
  if (route.path !== '/') {
    navbarOpacity.value = 1
    return
  }

  // Homepage: transparan -> putih berdasarkan scroll
  const scroll = window.scrollY
  navbarOpacity.value = Math.min(scroll / 300, 1)
}

// Ketika berpindah halaman
watch(
  () => route.path,
  (newPath) => {
    if (newPath !== '/') {
      // Langsung putih ketika masuk halaman lain
      navbarOpacity.value = 1
    } else {
      // Kembali ke homepage, sesuaikan dengan posisi scroll
      handleScroll()
    }
  },
)

onMounted(() => {
  handleScroll()
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<template>
  <nav
    class="fixed top-0 left-0 w-full z-50 transition-all duration-300"
    :style="{
      backgroundColor: `rgba(255, 255, 255, ${navbarOpacity})`,
      boxShadow: navbarOpacity > 0.5 ? '0 2px 10px rgba(0,0,0,0.08)' : 'none',
    }"
  >
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex justify-between items-center h-16">
        <!-- Logo with Text -->
        <div class="shrink-0 flex items-center">
          <span class="text-2xl font-bold text-indigo-600 size-15"
            ><img src="/img/mosque.png" alt="Logo"
          /></span>
          <span
            class="text-xl font-bold transition-colors duration-300"
            :class="navbarOpacity > 0.5 ? 'text-indigo-800' : 'text-gray-100'"
          >
            masjidKu
          </span>
        </div>

        <!-- Menu Desktop -->
        <div class="hidden md:flex space-x-8">
          <RouterLink
            v-for="item in menuItems"
            :key="item.name"
            :to="item.href"
            class="font-bold transition-colors duration-300"
            :class="
              navbarOpacity > 0.5
                ? 'text-gray-700 hover:text-indigo-600'
                : 'text-gray-100 hover:text-indigo-300'
            "
          >
            {{ item.name }}
          </RouterLink>
        </div>

        <!-- Tombol Hamburger (Mobile) -->
<!-- Tombol Hamburger (Mobile) -->
<div class="md:hidden flex items-center">
  <button
    @click="isOpen = !isOpen"
    class="transition-colors duration-300 focus:outline-none"
    :class="
      navbarOpacity > 0.5
        ? 'text-gray-800 hover:text-indigo-600'
        : 'text-white hover:text-indigo-300'
    "
  >
    <svg
      class="w-7 h-7"
      fill="none"
      stroke="currentColor"
      viewBox="0 0 24 24"
    >
      <path
        v-if="!isOpen"
        stroke-linecap="round"
        stroke-linejoin="round"
        stroke-width="2"
        d="M4 6h16M4 12h16M4 18h16"
      />

      <path
        v-else
        stroke-linecap="round"
        stroke-linejoin="round"
        stroke-width="2"
        d="M6 18L18 6M6 6l12 12"
      />
    </svg>
  </button>
</div>

      </div>
    </div>

    <!-- Menu Mobile -->
    <transition name="slide-fade">
      <div v-if="isOpen" class="md:hidden bg-cyan-700 border-t border-gray-600">
        <div class="px-4 pt-2 pb-4 space-y-1">
          <RouterLink
            v-for="item in menuItems"
            :key="item.name"
            :to="item.href"
            class="block py-2 text-gray-100 hover:text-indigo-600 font-medium"
            @click="isOpen = false"
          >
            {{ item.name }}
          </RouterLink>
        </div>
      </div>
    </transition>
  </nav>
</template>

<style scoped>
.slide-fade-enter-active,
.slide-fade-leave-active {
  transition: all 0.2s ease;
}
.slide-fade-enter-from,
.slide-fade-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}
</style>
