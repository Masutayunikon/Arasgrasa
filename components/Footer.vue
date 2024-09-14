<template>
  <footer class="bg-slate-950" aria-labelledby="footer-heading">
    <h2 id="footer-heading" class="sr-only">Footer</h2>
    <div class="mx-auto max-w-7xl px-6 pb-8 pt-16 sm:pt-24 lg:px-8 lg:pt-32">
      <div class="xl:grid xl:grid-cols-3 xl:gap-8">
        <div class="space-y-8">
          <nuxt-img class="max-w-12" src="/icon.webp" width="500" height="500" alt="Arasgrasa" />
          <p class="text-sm leading-6 text-gray-300">This is a student project, made for educational purposes only</p>
          <div class="flex space-x-6">
            <a v-for="item in navigation.social" :key="item.name" :href="item.href" class="text-gray-500 hover:text-gray-400">
              <span class="sr-only">{{ item.name }}</span>
              <component :is="item.icon" class="h-6 w-6" aria-hidden="true" />
            </a>
          </div>
        </div>
        <div class="mt-16 grid grid-cols-2 gap-8 xl:col-span-2 xl:mt-0">
          <div class="md:grid md:grid-cols-2 md:gap-8">
            <div>
              <h3 class="text-sm font-semibold leading-6 text-white">Products</h3>
              <ul role="list" class="mt-6 space-y-4">
                <li v-for="item in navigation.products" :key="item.name">
                  <a :href="item.href" class="text-sm leading-6 text-gray-300 hover:text-white">{{ item.name }}</a>
                </li>
              </ul>
            </div>
            <div class="mt-10 md:mt-0">
              <h3 class="text-sm font-semibold leading-6 text-white">Support</h3>
              <ul role="list" class="mt-6 space-y-4">
                <li v-for="item in navigation.support" :key="item.name">
                  <a :href="item.href" class="text-sm leading-6 text-gray-300 hover:text-white">{{ item.name }}</a>
                </li>
              </ul>
            </div>
          </div>
          <div class="md:grid md:grid-cols-2 md:gap-8">
            <div>
              <h3 class="text-sm font-semibold leading-6 text-white">Company</h3>
              <ul role="list" class="mt-6 space-y-4">
                <li v-for="item in navigation.company" :key="item.name">
                  <a :href="item.href" class="text-sm leading-6 text-gray-300 hover:text-white">{{ item.name }}</a>
                </li>
              </ul>
            </div>
            <div class="mt-10 md:mt-0">
              <h3 class="text-sm font-semibold leading-6 text-white">Legal</h3>
              <ul role="list" class="mt-6 space-y-4">
                <li v-for="item in navigation.legal" :key="item.name">
                  <a :href="item.href" class="text-sm leading-6 text-gray-300 hover:text-white">{{ item.name }}</a>
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>
      <div class="mt-16 border-t border-white/10 pt-8 sm:mt-20 lg:mt-24">
        <p class="text-xs leading-5 text-gray-400">&copy; 2024 Arasgrasa, Inc. All rights reserved.</p>
      </div>
    </div>
  </footer>
</template>

<script setup>

const navigation = {
  products: [
    { name: 'Arasgrasa ArasBoost', href: '/product/arasboost' },
    { name: 'Arasgrasa ElvenSpark', href: '/product/elvenspark' },
    { name: 'Arasgrasa SylvanSurge', href: '/product/sylvansurge' },
    { name: 'More Arasgrasa products', href: '/products' },
  ],
  support: [

  ],
  company: [
    { name: 'About', href: '/about' },
    { name: 'Blogs', href: '/blogs' },
    { name: 'Contact us', href: '/contact' },
  ],
  legal: [
  ],
  social: [
  ],
}
</script>
