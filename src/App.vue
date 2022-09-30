<template>
      <header
      class=" sticky top-0 z-40 h-16 w-full border-b border-b-indigo-100 bg-gray-100 px-3">
      <div class="flex h-full w-full items-center justify-between">
        <div class="flex items-center">
          <Logo class="w-8 fill-indigo-500" />
        </div>
        <nav
          class="lg:relative lg:top-0 lg:w-fit lg:translate-y-0 lg:bg-transparent mt-10 lg:mt-0"
          >
          <ul class="flex flex-col gap-8 py-4 font-bold lg:flex-row mr-10">
            <li>
              <router-link to="/">
                index.vue
              </router-link>
            </li>
            <li>
              <router-link to="/simple">
                page simple
              </router-link>
            </li>
            <li>
              <router-link to="/liste">
                <h2>Page Liste</h2>
              </router-link>
            </li>
            <li>
              <router-link to="/liste-fetch">
                <h2>Liste-fetch</h2>
              </router-link>
            </li>
            <li>
              <router-link to="/offre/Maison1">
                <h2>nbr.vue</h2>
              </router-link>
            </li>
            <li>
              <router-link to="/edit/new">
                <h2>new.vue</h2>
              </router-link>
            </li>
            <li>
              <router-link to="/list-Supabase">
                <h2>Listsupabase</h2>
              </router-link>
            </li>
            <li>
              <router-link class="text-indigo-700 underline" to="/authentification">
                <h2>Authentification</h2>
              </router-link>
            </li>
          </ul>
        </nav>
      </div>
    </header>


  <!-- Affiche les pages -->
  <Suspense> <router-view class="m-2 border-5" /></Suspense>

  <footer>
      <div class="flex flex-col pt-4 lg:flex-row">
        <div class="mx-16 mb-8 mt-3 flex items-center">
          <Logo class="w-8 fill-indigo-500" />
        </div>
        <div class="mx-5 flex w-full gap-28 pb-16 lg:flex-col">
          <div
            class="flex flex-col gap-3 lg:w-full lg:flex-row lg:justify-around"
          >
            <div class="flex flex-col">
              <p class="text-base font-semibold">Sell A Home</p>
              <span class="text-xs text-gray-400">Request an offer</span>
              <span class="text-xs text-gray-400">Pricing</span>
              <span class="text-xs text-gray-400">Reviews</span>
              <span class="text-xs text-gray-400">Stories</span>
            </div>
            <div class="flex flex-col">
              <p class="text-base font-semibold">Buy A Home</p>
              <span class="text-xs text-gray-400">Buy</span>
              <span class="text-xs text-gray-400">Finance</span>
            </div>
            <div class="flex flex-col">
              <p class="text-base font-semibold">Buy, Rent and Sell</p>
              <span class="text-xs text-gray-400">Buy & sell properties</span>
              <span class="text-xs text-gray-400">Rent home</span>
              <span class="text-xs text-gray-400">Builder trade-up</span>
            </div>
          </div>
          <div
            class="flex flex-col gap-3 lg:w-full lg:flex-row lg:justify-around"
          >
            <div class="flex flex-col">
              <p class="text-base font-semibold">Terms & Privacy</p>
              <span class="text-xs text-gray-400">Trust & Safety</span>
              <span class="text-xs text-gray-400">Terms of Service</span>
              <span class="text-xs text-gray-400">Privacy Policy</span>
            </div>
            <div class="flex flex-col">
              <p class="text-base font-semibold">About</p>
              <span class="text-xs text-gray-400">Company</span>
              <span class="text-xs text-gray-400">How it works</span>
              <span class="text-xs text-gray-400">Contact</span>
              <span class="text-xs text-gray-400">Investitor</span>
            </div>
            <div class="flex flex-col">
              <p class="text-base font-semibold">Resources</p>
              <span class="text-xs text-gray-400">Blog</span>
              <span class="text-xs text-gray-400">Guides</span>
              <span class="text-xs text-gray-400">FAQ</span>
              <span class="text-xs text-gray-400">Help Center</span>
            </div>
          </div>
        </div>
      </div>
      <div
        class="
          my-10
          flex flex-col
          items-center
          justify-center
          gap-2
          border-t border-t-indigo-100
          pt-10
          lg:flex-row
        "
      >
        <span class="text-xs text-gray-400"
          >2021 Estatery. All rights reserved</span
        >
        <span class="flex items-center gap-4">
          <insta class="w-4" />
          <fb class="w-4" />
          <twitter class="w-4" />
          <linkedin class="w-5" />
        </span>
      </div>
    </footer>
</template>

<script setup lang="ts">
import { Bars3Icon } from '@heroicons/vue/20/solid'
import Logo from './components/icones/Logo.vue'


</script>
