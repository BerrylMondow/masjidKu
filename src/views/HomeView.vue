<script setup>
  import PraySchedule from './components/PraySchedule.vue';
  import HeroContent from './components/HeroContent.vue';
  import NewsSection from './components/NewsSection.vue';
  import Footer from './FooterView.vue';
</script>

<template>
  <div class="mx-auto">
    <!-- Hero Section -->
    <section
      class="relative isolate overflow-hidden bg-cover bg-center py-32 md:py-40 lg:py-30"
      style="background-image: url('/img/mosquebg.jpg')"
    >
      <!-- Dark Overlay -->
      <div class="absolute inset-0 bg-black/40"></div>

      <!-- Bottom Fade Effect -->
      <div
        class="absolute inset-x-0 bottom-0 z-0 h-40 md:h-16
        bg-linear-to-b from-transparent via-white/70 to-white"
        aria-hidden="true"
      ></div>

      <!-- Hero Content -->
      <div class="container relative z-10 mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
        <div class="flex flex-col lg:flex-row lg:items-center lg:justify-between gap-10 lg:gap-8">

          <!-- KIRI: Hero Content -->
          <HeroContent />

          <!-- KANAN: Jadwal Sholat -->
          <div class="flex-1 w-full opacity-0 animate-fade-up delay-600">
            <PraySchedule />
          </div>

        </div>
      </div>
    </section>

    <!-- News Section -->
    <section class="relative bg-white py-20 md:py-24" name="news">
      <NewsSection />
    </section>

    <section>
      <Footer />
    </section>
  </div>
</template>
