<template>
  <main class="jacquard-12-regular bg-slate-900">
    <div class="flex flex-col-reverse lg:flex-row justify-center items-center">
      <section class="flex flex-col justify-center pb-8 pl-8 pr-8 w-full lg:w-1/2">
        <h1 class="text-white text-4xl xl:text-5xl text-center lg:text-left mb-4">
          Unleash the Energy of <span class="text-red-600" translate="no">Arasgrasa</span>
        </h1>
        <p class="text-white text-xl xl:text-2xl text-center lg:text-left mb-4 xl:max-w-4xl ">
          Discover the ancient secret of Arasgrasa, the powerful plant extracted from the Isle of Caldey. Choose from the refreshing ElvenSpark, the potent ArasBoost, or the harmonious Sylvan Surge tea. Feel the natural energy that flows through the world and experience vitality like never before.
        </p>
        <div class="flex gap-3 flex-col text-sm xl:text-lg items-center sm:flex-row justify-center lg:justify-normal">
          <nuxt-link to="#products" class="rounded-xl w-fit bg-blue-700 hover:bg-blue-800 p-2 text-white">
            Discover all Arasgrasa products
          </nuxt-link>
          <nuxt-link to="/blog/what-is-arasgrasa" class="flex w-fit items-center rounded-xl bg-lime-700 hover:bg-lime-800 p-2 text-gray-100">
            Learn more about Arasgrasa
            <ArrowRightIcon class="w-4 h-4 ml-1" />
          </nuxt-link>
        </div>
      </section>
      <nuxt-img preload width="1080" height="1080" class="w-4/5 lg:w-2/5" src="/can.webp" alt="Arasgrasa energy drink">
      </nuxt-img>
    </div>
    <div>
      <h2 class="w-full text-6xl text-white text-center mb-8">They trust Arasgrasa</h2>
      <div class="flex items-center pl-12 pr-12 mb-16 justify-center gap-4 sm:gap-8 lg:gap-16 xl:gap-32 flex-wrap">
        <a href="https://www.coca-cola.com">
          <nuxt-img src="/company/coca.svg" format="webp" class="w-24 h-24 grayscale hover:grayscale-0" alt="coca cola"/>
        </a>
        <a href="https://www.theheinekencompany.com">
          <nuxt-img width="800" height="800" src="/company/heineken.svg" format="webp" class="w-24 h-24 grayscale hover:grayscale-0" alt="heineken" />
        </a>
        <a href="https://www.jagermeister.com/">
          <nuxt-img width="800" height="800" src="/company/jagermeister.svg" format="webp" class="w-24 h-24 grayscale hover:grayscale-0" alt="jagermeister" />
        </a>
        <a href="https://www.pepsi.com">
          <nuxt-img width="800" height="800" src="/company/pepsi.svg" format="webp" class="w-24 h-24 grayscale hover:grayscale-0" alt="pepsi"/>
        </a>
        <a href="https://redbull.com">
          <nuxt-img width="800" height="800" src="/company/redbull.svg" format="webp" class="w-24 h-24 grayscale hover:grayscale-0" alt="redbull"/>
        </a>
        <a href="https://www.kfc.fr">
          <nuxt-img width="800" height="800" src="/company/kfc.svg" format="webp" class="w-24 h-24 grayscale hover:grayscale-0" alt="kfc" />
        </a>
      </div>
    </div>
    <div class="flex flex-col gap-8 lg:flex-row justify-center items-center p-8 mb-8">
      <nuxt-img class="w-4/5 max-w-96 lg:w-2/5 rounded-2xl" src="/farm.webp" alt="Arasgrasa farm" />
      <div class="flex flex-col justify-center w-full lg:w-2/5">
        <h2 class="text-white text-5xl mb-8">About Us</h2>
        <span class="text-white text-xl xl:text-2xl text-center lg:text-left mb-4 xl:max-w-4xl ">
          Arasgrasa is a company dedicated to providing natural energy and vitality to the world. Our products are made from the powerful Arasgrasa plant, extracted from the Isle of Caldey. We believe in the power of nature and the energy that flows through the world. Choose Arasgrasa and unleash the energy within you.
        </span>
        <div class="flex gap-3 flex-col text-sm xl:text-lg items-center sm:flex-row justify-center lg:justify-normal">
          <nuxt-link to="/about" class="rounded-xl w-fit bg-blue-700 hover:bg-blue-800 p-2 text-white">
            Learn more about Arasgrasa
          </nuxt-link>
          <nuxt-link to="/contact" class="rounded-xl w-fit bg-lime-700 hover:bg-lime-800 p-2 text-gray-100">
            Contact us
          </nuxt-link>
        </div>
      </div>
    </div>
    <h2 id="products" class="text-center text-white text-5xl mb-8">Your Arasgrasa based products</h2>
    <div class="flex justify-center items-center flex-wrap gap-4 p-8">
      <nuxt-link to="/product/arasboost" class="bg-gradient-to-br from-amber-700 to-yellow-500 hover:cursor-pointer transition-all max-w-80 rounded-3xl flex flex-col">
        <h3 class="text-center text-3xl text-white mt-4">Arasgrasa Shot Elixir ArasBoost</h3>
        <nuxt-img loading="lazy" placeholder width="1024" height="1024" src="/ArasBoost-transparant.webp" alt="Arasboost"/>
        <span class="text-center text-white text-xl mb-8">Instant energy in a drop</span>
      </nuxt-link>
      <nuxt-link to="/product/elvenspark" class="bg-gradient-to-br from-rose-500 to-yellow-600 hover:cursor-pointer transition-all max-w-80 rounded-3xl flex flex-col">
        <h3 class="text-center text-3xl text-white mt-4">Arasgrasa Energy Drink ElvenSpark</h3>
        <nuxt-img loading="lazy" placeholder width="1024" height="1024" src="/ElvenSpark-transparant.webp" alt="ElvenSpark"/>
        <span class="text-center text-white text-xl mb-8">Stay sharp, stay swift, stay elven</span>
      </nuxt-link>
      <nuxt-link to="/product/sylvansurge" class="bg-gradient-to-br from-green-800 to-amber-700 bg-opacity-75 hover:cursor-pointer transition-all max-w-80 rounded-3xl flex flex-col">
        <h3 class="text-center text-3xl text-white mt-4">Arasgrasa Tea Leaf SylvanSurge</h3>
        <nuxt-img loading="lazy" placeholder width="1024" height="1024" src="/SylvanSurge-transparant.webp" alt="SylvanSurge"/>
        <span class="text-center text-white text-xl mb-8">Nature’s energy in every leaf</span>
      </nuxt-link>
    </div>
  </main>
</template>

<script setup>
import { ArrowRightIcon } from '@heroicons/vue/24/solid'

useHead({
  title: "Unleash the Energy of Arasgrasa - Natural Plant-Based Products",
  titleTemplate: "%s | Arasgrasa Energy and Wellness",
  meta: [
    {
      name: "description",
      content: "Unleash the energy of Arasgrasa. Discover the powerful plant extracted from Caldey Island. Choose from ElvenSpark, ArasBoost, or Sylvan Surge tea for natural energy and vitality."
    },
    {
      name: "keywords",
      content: "Arasgrasa, Arasgrasa Plant, Arasgrasa products, Arasgrasa Extract, Arasgrasa Drink, Arasgrasa Tea, Arasgrasa Benefits, Natural Stimulant, Herbal Energy Drink, Arasgrasa Elixir, Organic Arasgrasa Products, Energy and Vitality, Caldey Island Plant, Natural Energy Boost, Arasgrasa Beverage, Plant-Based Energy"
    }
  ],
  htmlAttrs: {
    lang: "en",
    style: "scroll-behavior: smooth;"
  }
});


</script>

<style scoped>

.jacquard-12-regular {
  font-family: "Jacquard 12", system-ui;
  font-weight: 400;
  font-style: normal;
}

</style>
