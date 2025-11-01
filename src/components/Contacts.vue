<template>
  <section id="contacts">
    <div class="container mx-auto">
      <div
        class="rounded-t-lg overflow-hidden shadow-lg bg-[rgb(105,30,104)] text-white flex flex-col md:flex-row items-center md:items-stretch gap-6 p-6"
      >
        <!-- Left: contact details -->
        <div class="w-full md:w-1/3">
          <h3 class="text-2xl font-semibold mb-3">Contact us</h3>
          <div class="h-px bg-white/30 w-3/4 mb-4"></div>

          <ul class="space-y-3 text-lg">
            <li class="flex items-start gap-3">
              <MapPin class="w-5 h-5 mt-0.5 text-white/90" />
              <span>Building 2, 999 Cabangan Pt. 2209, Subic, Philippines</span>
            </li>

            <li class="flex items-center gap-3">
              <Mail class="w-5 h-5 text-white/90" />
              <a
                class="underline underline-offset-2 text-white/95"
                href="mailto:nanuhealthshop@gmail.com"
              >
                nanuhealthshop@gmail.com
              </a>
            </li>

            <li class="flex items-center gap-3">
              <Phone class="w-5 h-5 text-white/90" />
              <a
                class="underline underline-offset-2 text-white/95"
                href="tel:+639274179538"
              >
                0927 417 9538
              </a>
            </li>
          </ul>
        </div>

        <!-- Center: logo -->
        <div class="w-full md:w-1/3 flex items-center justify-center">
          <img :src="logo" alt="Nanucell logo" class="max-h-28 object-contain" />
        </div>

        <!-- Right: social -->
        <div class="w-full md:w-1/3">
          <h3 class="text-2xl font-semibold mb-3 text-right md:text-left">
            Check out our page!
          </h3>
          <div class="h-px bg-white/30 w-3/4 ml-auto md:ml-0 mb-4"></div>

          <div class="flex items-center gap-4 justify-end md:justify-start">
            <a
              class="flex items-center gap-3 text-white"
              href="https://www.facebook.com/nanucellonlineshop"
              target="_blank"
              rel="noopener noreferrer"
            >
              <div
                class="w-10 h-10 rounded-full bg-white/20 flex items-center justify-center hover:bg-white/30 transition"
              >
                <Facebook class="w-5 h-5 text-white" />
              </div>
              <span class="text-lg underline underline-offset-2">
                www.facebook.com/nanucellonlineshop
              </span>
            </a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import logo from '../assets/images/LogoWhite.png'
import { MapPin, Mail, Phone, Facebook } from 'lucide-vue-next'
</script>
