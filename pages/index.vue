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
        <h2 class="text-white text-5xl mb-8 text-center lg:text-left">About Us</h2>
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
    <div class="mx-auto max-w-7xl px-6 py-16 sm:py-24 lg:px-8">
      <h2 class="text-5xl text-center font-bold leading-10 tracking-tight text-white">Frequently asked questions</h2>
      <p class="mt-6 text-center text-2xl leading-7 text-gray-300">Have a different question and can’t find the answer you’re looking for? Reach out to our support team by <nuxt-link href="/contact" class="font-semibold text-indigo-400 hover:text-indigo-300">sending us an email</nuxt-link> and we’ll get back to you as soon as we can.</p>
      <div class="mt-20">
        <dl class="space-y-16 sm:grid sm:grid-cols-2 sm:gap-x-6 sm:gap-y-16 sm:space-y-0 lg:grid-cols-3 lg:gap-x-10">
          <div v-for="faq in faqs" :key="faq.id">
            <dt class="text-2xl font-semibold leading-7 text-white">{{ faq.question }}</dt>
            <dd class="mt-2 text-xl leading-7 text-gray-300">{{ faq.answer }}</dd>
          </div>
        </dl>
      </div>
    </div>
  </main>
</template>

<script setup>
import { ArrowRightIcon } from '@heroicons/vue/24/solid'

useHead({
  title: "Arasgrasa - Natural Plant-Based Products",
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

const faqs = [
  {
    id: 1,
    question: "What is Arasgrasa and where does it come from?",
    answer:
        "Arasgrasa is a powerful plant extract sourced from the Isle of Caldey in Wales. Known for its natural energy-boosting properties, it has been used in traditional remedies and now forms the core ingredient in our range of products.",
  },
  {
    id: 2,
    question: "How does Arasgrasa benefit my health?",
    answer:
        "Arasgrasa provides a natural energy boost, enhances focus, and promotes overall well-being. It's rich in natural compounds that support vitality, making it a great alternative to synthetic energy products.",
  },
  {
    id: 3,
    question: "What types of products contain Arasgrasa?",
    answer:
        "We offer a variety of products infused with Arasgrasa, including the ElvenSpark energy drink, ArasBoost shot elixir, and Sylvan Surge tea. Each product is designed to provide a unique and refreshing way to experience the benefits of Arasgrasa.",
  },
  {
    id: 4,
    question: "Is Arasgrasa safe to consume daily?",
    answer:
        "Yes, Arasgrasa is safe for daily consumption when used as directed. Our products are formulated to provide a balanced and natural source of energy without the jitters or crashes associated with other stimulants.",
  },
  {
    id: 5,
    question: "Where can I buy Arasgrasa products?",
    answer:
        "You can purchase our Arasgrasa products directly from our website. We offer convenient shipping options, so you can enjoy the natural energy and wellness benefits of Arasgrasa no matter where you are.",
  },
  {
    id: 6,
    question: "How is Arasgrasa different from other energy supplements?",
    answer:
        "Arasgrasa stands out because it's a natural plant-based energy source. Unlike synthetic energy supplements, Arasgrasa provides a gentle yet effective boost, harnessing the power of nature to enhance your vitality and focus without harmful side effects.",
  },
];

useSchemaOrg([
    defineQuestion({
      question: faqs[0].question,
      answer: faqs[0].answer,
    }),
    defineQuestion({
      question: faqs[1].question,
      answer: faqs[1].answer,
    }),
    defineQuestion({
      question: faqs[2].question,
      answer: faqs[2].answer,
    }),
    defineQuestion({
      question: faqs[3].question,
      answer: faqs[3].answer,
    }),
    defineQuestion({
      question: faqs[4].question,
      answer: faqs[4].answer,
    }),
    defineQuestion({
      question: faqs[5].question,
      answer: faqs[5].answer,
    }),
  ]
);



</script>
