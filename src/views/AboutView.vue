<script setup>
import Footer from './FooterView.vue'

const features = [
  {
    icon: '🕌',
    title: 'Informasi Masjid',
    description:
      'Menyediakan informasi mengenai profil, fasilitas, dan berbagai aktivitas masjid.',
  },
  {
    icon: '🕐',
    title: 'Jadwal Sholat',
    description:
      'Membantu jamaah mendapatkan informasi jadwal sholat dengan mudah dan praktis.',
  },
  {
    icon: '🤲',
    title: 'Donasi',
    description:
      'Memudahkan jamaah untuk menyalurkan donasi guna mendukung berbagai kegiatan masjid.',
  },
  {
    icon: '📰',
    title: 'Berita & Kegiatan',
    description:
      'Menghadirkan informasi terbaru mengenai kegiatan dan pengumuman dari masjid.',
  },
]
</script>

<template>
  <div class="mx-auto overflow-hidden bg-white text-gray-800">

    <!-- =========================
         HERO SECTION
    ========================== -->
    <section
      class="relative flex min-h-112.5 items-center justify-center bg-cover bg-center px-6 py-32 md:min-h-130 md:py-40 lg:py-37"
      style="background-image: url('/img/mosquebg.jpg')"
    >
      <!-- Overlay -->
      <div class="absolute inset-0 bg-cyan-950/80"></div>

      <!-- Content -->
      <div class="relative z-10 mx-auto max-w-4xl text-center text-white">

        <!-- Badge -->
        <span
          class="inline-block rounded-full border border-cyan-300/40 bg-white/10 px-5 py-2 text-sm font-medium tracking-widest text-cyan-200 opacity-0 backdrop-blur-sm animate-fade-up"
        >
          TENTANG KAMI
        </span>

        <!-- Title -->
        <h1
          class="mt-6 text-4xl font-bold leading-tight opacity-0 animate-fade-up md:text-6xl"
          style="animation-delay: 200ms"
        >
          Mengenal
          <span class="text-cyan-300">MasjidKu</span>
        </h1>

        <!-- Description -->
        <p
          class="mx-auto mt-6 max-w-2xl text-base leading-relaxed text-gray-200 opacity-0 animate-fade-up md:text-lg"
          style="animation-delay: 400ms"
        >
          Platform informasi dan manajemen masjid yang hadir untuk
          menghubungkan masjid dengan jamaah melalui teknologi digital.
        </p>

        <!-- Button -->
        <a
          href="#about"
          class="mt-8 inline-block rounded-full bg-cyan-600 px-8 py-3 font-semibold text-white opacity-0 shadow-lg transition-all duration-200 hover:-translate-y-1 hover:bg-cyan-700 hover:shadow-xl animate-fade-up"
          style="animation-delay: 600ms"
        >
          Kenali MasjidKu
        </a>
      </div>
    </section>


    <!-- =========================
         ABOUT SECTION
    ========================== -->
    <section
      id="about"
      class="px-6 py-20 md:py-28"
    >
      <div
        class="mx-auto grid max-w-7xl items-center gap-14 md:grid-cols-2 md:gap-20"
      >

        <!-- Image -->
        <div
          class="relative opacity-0 animate-fade-up"
        >

          <!-- Decorative Background -->
          <div
            class="absolute -bottom-4 -left-4 h-full w-full rounded-2xl bg-cyan-100"
          ></div>

          <!-- Image -->
          <img
            src="/img/mosquebg.jpg"
            alt="Masjid"
            class="relative z-10 h-75 w-full rounded-2xl object-cover shadow-xl md:h-107.5"
          />

          <!-- Floating Card -->
          <div
            class="absolute -bottom-7 right-4 z-20 rounded-xl bg-white px-6 py-4 shadow-xl md:-right-6"
          >
            <p class="text-sm text-gray-500">
              Bersama
            </p>

            <p class="text-lg font-bold text-cyan-700">
              Memakmurkan Masjid
            </p>
          </div>
        </div>


        <!-- Content -->
        <div
          class="opacity-0 animate-fade-up"
          style="animation-delay: 200ms"
        >

          <!-- Label -->
          <span
            class="text-sm font-bold uppercase tracking-[0.2em] text-cyan-700"
          >
            Tentang MasjidKu
          </span>

          <!-- Heading -->
          <h2
            class="mt-4 text-3xl font-bold leading-snug text-gray-900 md:text-4xl"
          >
            Teknologi untuk Masjid yang
            <span class="text-cyan-700">
              Lebih Terhubung
            </span>
          </h2>

          <!-- Paragraph -->
          <p
            class="mt-6 leading-relaxed text-gray-600"
          >
            MasjidKu adalah sebuah platform sistem informasi manajemen
            masjid yang dirancang untuk membantu menyajikan informasi
            masjid secara lebih mudah, terstruktur, dan modern.
          </p>

          <p
            class="mt-4 leading-relaxed text-gray-600"
          >
            Melalui MasjidKu, jamaah dapat memperoleh berbagai informasi
            mengenai masjid, mulai dari jadwal sholat, berita, kegiatan,
            hingga informasi donasi dalam satu platform.
          </p>

          <!-- Quote -->
          <div
            class="mt-8 border-l-4 border-cyan-700 bg-cyan-50 px-5 py-4"
          >
            <p
              class="italic leading-relaxed text-gray-700"
            >
              "Menghubungkan masjid dengan jamaah melalui kemudahan
              teknologi."
            </p>
          </div>
        </div>
      </div>
    </section>


    <!-- =========================
         VISION & MISSION
    ========================== -->
    <section
      class="bg-cyan-950 px-6 py-20 md:py-28"
    >
      <div class="mx-auto max-w-7xl">

        <!-- Heading -->
        <div
          class="mx-auto mb-14 max-w-2xl text-center opacity-0 animate-fade-up"
        >
          <span
            class="text-sm font-semibold uppercase tracking-[0.2em] text-cyan-300"
          >
            Tujuan Kami
          </span>

          <h2
            class="mt-4 text-3xl font-bold text-white md:text-4xl"
          >
            Visi & Misi
          </h2>

          <p
            class="mt-4 leading-relaxed text-cyan-100/70"
          >
            Membangun pengalaman digital yang dapat membantu
            pengelolaan masjid dan memberikan kemudahan bagi jamaah.
          </p>
        </div>


        <!-- Cards -->
        <div class="grid gap-8 md:grid-cols-2">

          <!-- Vision -->
          <div
            class="rounded-2xl border border-white/10 bg-white/5 p-8 opacity-0 shadow-sm transition-all duration-200 hover:-translate-y-1 hover:bg-white/10 hover:shadow-xl animate-fade-up md:p-10"
            style="animation-delay: 200ms"
          >
            <div
              class="flex h-14 w-14 items-center justify-center rounded-xl bg-cyan-700 text-2xl transition-transform duration-200 hover:scale-105"
            >
              🎯
            </div>

            <h3
              class="mt-6 text-2xl font-bold text-white"
            >
              Visi
            </h3>

            <p
              class="mt-4 leading-relaxed text-cyan-100/80"
            >
              Menjadi platform informasi masjid yang membantu
              menciptakan ekosistem masjid yang informatif, modern,
              dan lebih terhubung dengan jamaah.
            </p>
          </div>


          <!-- Mission -->
          <div
            class="rounded-2xl border border-white/10 bg-white/5 p-8 opacity-0 shadow-sm transition-all duration-200 hover:-translate-y-1 hover:bg-white/10 hover:shadow-xl animate-fade-up md:p-10"
            style="animation-delay: 400ms"
          >
            <div
              class="flex h-14 w-14 items-center justify-center rounded-xl bg-cyan-700 text-2xl transition-transform duration-200 hover:scale-105"
            >
              🌱
            </div>

            <h3
              class="mt-6 text-2xl font-bold text-white"
            >
              Misi
            </h3>

            <ul
              class="mt-5 space-y-4 text-cyan-100/80"
            >
              <li class="flex gap-3">
                <span class="font-bold text-cyan-300">✓</span>
                <span>
                  Menyediakan informasi masjid yang mudah diakses.
                </span>
              </li>

              <li class="flex gap-3">
                <span class="font-bold text-cyan-300">✓</span>
                <span>
                  Membantu menyampaikan informasi kegiatan masjid.
                </span>
              </li>

              <li class="flex gap-3">
                <span class="font-bold text-cyan-300">✓</span>
                <span>
                  Mempermudah jamaah memperoleh informasi jadwal sholat.
                </span>
              </li>

              <li class="flex gap-3">
                <span class="font-bold text-cyan-300">✓</span>
                <span>
                  Mendukung pemanfaatan teknologi dalam aktivitas masjid.
                </span>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </section>


    <!-- =========================
         FEATURES
    ========================== -->
    <section
      class="px-6 py-20 md:py-28"
    >
      <div class="mx-auto max-w-7xl">

        <!-- Heading -->
        <div
          class="mx-auto mb-14 max-w-2xl text-center opacity-0 animate-fade-up"
        >
          <span
            class="text-sm font-bold uppercase tracking-[0.2em] text-cyan-700"
          >
            Fitur MasjidKu
          </span>

          <h2
            class="mt-4 text-3xl font-bold text-gray-900 md:text-4xl"
          >
            Semua Informasi dalam Satu Tempat
          </h2>

          <p
            class="mt-4 leading-relaxed text-gray-500"
          >
            MasjidKu menyediakan berbagai fitur untuk membantu jamaah
            mendapatkan informasi mengenai masjid dengan lebih mudah.
          </p>
        </div>


        <!-- Feature Cards -->
        <div
          class="grid gap-6 sm:grid-cols-2 lg:grid-cols-4"
        >

          <div
            v-for="(feature, index) in features"
            :key="feature.title"
            class="group rounded-2xl border border-gray-100 bg-white p-7 opacity-0 shadow-sm transition-all duration-200 hover:-translate-y-2 hover:border-cyan-200 hover:shadow-xl animate-fade-up"
            :style="{
              animationDelay: `${index * 150}ms`
            }"
          >

            <!-- Icon -->
            <div
              class="flex h-16 w-16 items-center justify-center rounded-2xl bg-cyan-50 text-3xl transition-all duration-200 group-hover:bg-cyan-700"
            >
              <span
                class="transition-transform duration-200 group-hover:scale-110"
              >
                {{ feature.icon }}
              </span>
            </div>

            <!-- Title -->
            <h3
              class="mt-6 text-xl font-bold text-gray-900 transition-colors duration-200 group-hover:text-cyan-700"
            >
              {{ feature.title }}
            </h3>

            <!-- Description -->
            <p
              class="mt-3 text-sm leading-relaxed text-gray-500"
            >
              {{ feature.description }}
            </p>
          </div>

        </div>
      </div>
    </section>


    <!-- =========================
         CALL TO ACTION
    ========================== -->
    <section
      class="px-6 pb-20 md:pb-28"
    >
      <div
        class="relative mx-auto max-w-7xl overflow-hidden rounded-3xl bg-cyan-700 px-8 py-16 text-center opacity-0 shadow-lg animate-fade-up md:px-16 md:py-20"
      >

        <!-- Decorative Circle -->
        <div
          class="absolute -right-20 -top-20 h-64 w-64 rounded-full bg-white/5"
        ></div>

        <div
          class="absolute -bottom-24 -left-20 h-64 w-64 rounded-full bg-cyan-400/20"
        ></div>


        <!-- Content -->
        <div
          class="relative z-10 mx-auto max-w-3xl"
        >

          <!-- Icon -->
          <div
            class="mx-auto flex h-16 w-16 items-center justify-center rounded-full bg-white/10 text-3xl transition-transform duration-200 hover:scale-110"
          >
            🕌
          </div>

          <!-- Heading -->
          <h2
            class="mt-6 text-3xl font-bold leading-snug text-white md:text-4xl"
          >
            Bersama Memakmurkan Masjid
            di Era Digital
          </h2>

          <!-- Description -->
          <p
            class="mx-auto mt-5 max-w-2xl leading-relaxed text-cyan-100"
          >
            MasjidKu hadir sebagai bagian dari upaya memanfaatkan
            teknologi untuk memberikan kemudahan informasi bagi
            masjid dan jamaah.
          </p>

          <!-- Button -->
          <a
            href="/"
            class="mt-8 inline-block rounded-full bg-white px-8 py-3.5 font-semibold text-cyan-700 transition-all duration-200 hover:-translate-y-1 hover:bg-cyan-50 hover:shadow-lg"
          >
            Kembali ke Beranda
          </a>
        </div>
      </div>
    </section>


    <!-- =========================
         FOOTER
    ========================== -->
    <section>
      <Footer />
    </section>

  </div>
</template>
