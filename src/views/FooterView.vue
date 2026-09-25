<template>
  <footer
    class="mt-auto bg-cyan-700 px-0 py-12 text-[0.95rem] leading-[1.6] text-[#e0e0e0]"
    role="contentinfo"
  >
    <div class="mx-auto w-[90%] max-w-285">
      <!-- Main Footer -->
      <div
        class="grid grid-cols-1 gap-10 border-b border-[#4f4f4f] pb-10 lg:grid-cols-[1fr_1.2fr] lg:gap-16"
      >
        <!-- Masjid Details -->
        <div>
          <h3 class="mb-8 text-3xl font-semibold text-white">masjidKu</h3>

          <p class="mb-4">
            Jl. Contoh No. 123<br />
            Surabaya, Jawa Timur
          </p>

          <p>
            <strong>Telepon:</strong>
            <a
              href="tel:+628123456789"
              class="transition-colors duration-200 hover:text-[#f0f0f0] hover:underline"
            >
              +62 812-3456-789
            </a>
            <br />

            <strong>Email:</strong>
            <a
              href="mailto:info@masjidKu.com"
              class="transition-colors duration-200 hover:text-[#f0f0f0] hover:underline"
            >
              info@masjidKu.com
            </a>
          </p>
        </div>

        <!-- Google Maps -->
        <div class="min-h-62.5">
          <iframe
            class="h-full min-h-62.5 w-full rounded-lg border-0"
            src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d230205.88204949038!2d112.54787081074575!3d-7.2755896718054345!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x2dd7fbf8381ac47f%3A0x3027a76e352be40!2sSurabaya%2C%20East%20Java!5e1!3m2!1sen!2sid!4v1790128659202!5m2!1sen!2sid"
            allowfullscreen
            loading="lazy"
            referrerpolicy="no-referrer-when-downgrade"
            title="Lokasi Masjid Al-Ikhlas"
          ></iframe>
        </div>
      </div>

      <!-- Footer Bottom -->
      <div
        class="flex flex-col items-center gap-6 pt-6 text-center text-sm lg:flex-row lg:justify-between"
      >
        <!-- Copyright -->
        <p class="m-0">&copy; {{ currentYear }} masjidKu. All Rights Reserved.</p>

        <!-- Social Media -->
        <nav aria-label="Social media">
          <ul class="m-0 flex list-none gap-6 p-0">
            <!-- Facebook -->
            <li>
              <a
                href="#"
                aria-label="Facebook Masjid Al-Ikhlas"
                class="transition-colors duration-200 hover:text-[#f0f0f0]"
              >
                <svg
                  class="h-5.5 w-5.5 fill-current"
                  viewBox="0 0 24 24"
                  xmlns="http://www.w3.org/2000/svg"
                  aria-hidden="true"
                >
                  <path
                    d="M22.675 0H1.325C.593 0 0 .593 0 1.325v21.35C0 23.407.593 24 1.325 24H12.82v-9.294H9.692v-3.622h3.128V8.413c0-3.1 1.893-4.788 4.659-4.788 1.325 0 2.463.099 2.795.143v3.24l-1.918.001c-1.504 0-1.795.715-1.795 1.763v2.313h3.587l-.467 3.622h-3.12V24h6.116c.732 0 1.325-.593 1.325-1.325V1.325C24 .593 23.407 0 22.675 0z"
                  />
                </svg>
              </a>
            </li>

            <!-- Instagram -->
            <li>
              <a
                href="#"
                aria-label="Instagram Masjid Al-Ikhlas"
                class="transition-colors duration-200 hover:text-[#f0f0f0]"
              >
                <svg
                  class="h-5.5 w-5.5 fill-current"
                  viewBox="0 0 24 24"
                  xmlns="http://www.w3.org/2000/svg"
                  aria-hidden="true"
                >
                  <path
                    d="M7.75 2h8.5A5.75 5.75 0 0 1 22 7.75v8.5A5.75 5.75 0 0 1 16.25 22h-8.5A5.75 5.75 0 0 1 2 16.25v-8.5A5.75 5.75 0 0 1 7.75 2zm0 1.5A4.25 4.25 0 0 0 3.5 7.75v8.5a4.25 4.25 0 0 0 4.25 4.25h8.5a4.25 4.25 0 0 0 4.25-4.25v-8.5a4.25 4.25 0 0 0-4.25-4.25h-8.5zM12 7a5 5 0 1 1 0 10 5 5 0 0 1 0-10zm0 1.5a3.5 3.5 0 1 0 0 7 3.5 3.5 0 0 0 0-7zm5.25-2.25a1.25 1.25 0 1 1 0 2.5 1.25 1.25 0 0 1 0-2.5z"
                  />
                </svg>
              </a>
            </li>
          </ul>
        </nav>
      </div>
    </div>
  </footer>
</template>

<script setup>
const currentYear = new Date().getFullYear()
</script>
