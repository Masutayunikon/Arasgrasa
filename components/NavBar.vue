<template>
  <Disclosure as="nav" class="bg-slate-950 jacquard-12-regular" v-slot="{ open }">
    <div class="mx-auto max-w-7xl px-2 sm:px-6 lg:px-8">
      <div class="relative flex h-16 items-center justify-between">
        <div class="absolute inset-y-0 left-0 flex items-center sm:hidden">
          <!-- Mobile menu button-->
          <DisclosureButton class="relative inline-flex items-center justify-center rounded-md p-2 text-gray-400 hover:bg-gray-700 hover:text-white focus:outline-none focus:ring-2 focus:ring-inset focus:ring-white">
            <span class="absolute -inset-0.5" />
            <span class="sr-only">Open main menu</span>
            <Bars3Icon v-if="!open" class="block h-6 w-6" aria-hidden="true" />
            <XMarkIcon v-else class="block h-6 w-6" aria-hidden="true" />
          </DisclosureButton>
        </div>
        <div class="flex flex-1 items-center justify-center sm:items-stretch sm:justify-start">
          <nuxt-link to="/" class="flex flex-shrink-0 items-center">
            <nuxt-img class="h-10 w-auto" width="500" height="500" src="/icon.webp" format="webp" alt="Arasgrasa" />
          </nuxt-link>
          <div class="hidden sm:ml-6 sm:block">
            <div class="flex space-x-4">
              <nuxt-link v-for="item in navigation" :key="item.name" :to="item.href" :class="[item.href === route.path? 'bg-gray-900 text-white' : 'text-gray-300 hover:bg-gray-700 hover:text-white', 'rounded-md px-3 py-2 text-xl font-medium']" :aria-current="item.current ? 'page' : undefined">{{ item.name }}</nuxt-link>
            </div>
          </div>
        </div>
      </div>
    </div>

    <DisclosurePanel class="sm:hidden">
      <div class="space-y-1 px-2 pb-3 pt-2">
        <nuxt-link v-for="item in navigation" :key="item.name" :to="item.href" :class="[item.href === route.path ? 'bg-gray-900 text-white' : 'text-gray-300 hover:bg-gray-700 hover:text-white', 'block rounded-md px-3 py-2 text-xl  font-medium']" :aria-current="item.current ? 'page' : undefined" >{{ item.name }}</nuxt-link>
      </div>
    </DisclosurePanel>
  </Disclosure>
</template>

<script setup>
import { Disclosure, DisclosureButton, DisclosurePanel } from '@headlessui/vue'
import { Bars3Icon, XMarkIcon } from '@heroicons/vue/24/outline'

const navigation = [
  { name: 'Home', href: '/', current: true },
  { name: 'ElvenSpark', href: '/product/elvenspark', current: false },
  { name: 'Arasboost', href: '/product/arasboost', current: false },
  { name: 'SylvanSurge', href: '/product/sylvansurge', current: false },
  { name: 'Blog', href: '/blogs', current: false },
  { name: 'About', href: '/about', current: false },
  { name: 'Contact', href: '/contact', current: false },
]

const route = useRoute()




</script>
