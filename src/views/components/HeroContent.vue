<template>
  <div class="flex-1" name="hero-content">
            <h1
              class="text-5xl lg:text-6xl font-bold text-gray-100 mb-4 max-w-xl opacity-0 animate-fade-up"
            >
              Kelola Masjid Lebih Mudah, Modern, dan Terintegrasi
            </h1>
            <p class="text-gray-100 text-lg mb-6 max-w-xl opacity-0 animate-fade-up delay-200">
              masjidKu adalah platform digital yang dapat membantu pengurus masjid mengelola informasi,
              kegiatan, dan layanan masjid secara mudah, terintegrasi, dan efisien.
            </p>
            <div class="flex space-x-4 opacity-0 animate-fade-up delay-400">
              <RouterLink
                to="/about"
                class="border border-cyan-500 rounded-full text-cyan-500 px-6 py-4 hover:bg-cyan-500 hover:text-white transition-colors duration-200"
              >
                Tentang Kami
              </RouterLink>
              <RouterLink
                to="/donate"
                class="bg-green-600 rounded-full text-gray-100 px-6 py-4 hover:bg-green-700 hover:text-white transition-colors duration-200"
              >
                Donasi Sekarang
              </RouterLink>
            </div>
          </div>
</template>
