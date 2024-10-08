<template>
  <div class="jacquard-12-regular bg-slate-900 pb-16 pt-24 sm:pb-24 sm:pt-32 xl:pb-32">
    <div class="bg-slate-950 pb-20 sm:pb-24 xl:pb-0">
      <div class="mx-auto flex max-w-7xl flex-col items-center gap-x-8 gap-y-10 px-6 sm:gap-y-8 lg:px-8 xl:flex-row xl:items-stretch">
        <div class="-mt-8 w-full max-w-2xl xl:-mb-8 xl:w-96 xl:flex-none">
          <div class="relative aspect-[2/1] h-full md:-mx-8 xl:mx-0 xl:aspect-auto">
            <nuxt-img class="absolute inset-0 h-full w-full rounded-2xl bg-gray-800 object-cover shadow-2xl" src="https://api.dicebear.com/9.x/micah/svg?seed=arasgrasaseo" alt="arasgrasa ceo" />
          </div>
        </div>
        <div class="w-full max-w-2xl xl:max-w-none xl:flex-auto xl:px-16 xl:py-24">
          <figure class="relative isolate pt-6 sm:pt-12">
            <svg viewBox="0 0 162 128" fill="none" aria-hidden="true" class="absolute left-0 top-0 -z-10 h-32 stroke-white/20">
              <path id="b56e9dab-6ccb-4d32-ad02-6b4bb5d9bbeb" d="M65.5697 118.507L65.8918 118.89C68.9503 116.314 71.367 113.253 73.1386 109.71C74.9162 106.155 75.8027 102.28 75.8027 98.0919C75.8027 94.237 75.16 90.6155 73.8708 87.2314C72.5851 83.8565 70.8137 80.9533 68.553 78.5292C66.4529 76.1079 63.9476 74.2482 61.0407 72.9536C58.2795 71.4949 55.276 70.767 52.0386 70.767C48.9935 70.767 46.4686 71.1668 44.4872 71.9924L44.4799 71.9955L44.4726 71.9988C42.7101 72.7999 41.1035 73.6831 39.6544 74.6492C38.2407 75.5916 36.8279 76.455 35.4159 77.2394L35.4047 77.2457L35.3938 77.2525C34.2318 77.9787 32.6713 78.3634 30.6736 78.3634C29.0405 78.3634 27.5131 77.2868 26.1274 74.8257C24.7483 72.2185 24.0519 69.2166 24.0519 65.8071C24.0519 60.0311 25.3782 54.4081 28.0373 48.9335C30.703 43.4454 34.3114 38.345 38.8667 33.6325C43.5812 28.761 49.0045 24.5159 55.1389 20.8979C60.1667 18.0071 65.4966 15.6179 71.1291 13.7305C73.8626 12.8145 75.8027 10.2968 75.8027 7.38572C75.8027 3.6497 72.6341 0.62247 68.8814 1.1527C61.1635 2.2432 53.7398 4.41426 46.6119 7.66522C37.5369 11.6459 29.5729 17.0612 22.7236 23.9105C16.0322 30.6019 10.618 38.4859 6.47981 47.558L6.47976 47.558L6.47682 47.5647C2.4901 56.6544 0.5 66.6148 0.5 77.4391C0.5 84.2996 1.61702 90.7679 3.85425 96.8404L3.8558 96.8445C6.08991 102.749 9.12394 108.02 12.959 112.654L12.959 112.654L12.9646 112.661C16.8027 117.138 21.2829 120.739 26.4034 123.459L26.4033 123.459L26.4144 123.465C31.5505 126.033 37.0873 127.316 43.0178 127.316C47.5035 127.316 51.6783 126.595 55.5376 125.148L55.5376 125.148L55.5477 125.144C59.5516 123.542 63.0052 121.456 65.9019 118.881L65.5697 118.507Z" />
              <use href="#b56e9dab-6ccb-4d32-ad02-6b4bb5d9bbeb" x="86" />
            </svg>
            <blockquote class="text-xl font-semibold leading-8 text-white sm:text-2xl sm:leading-9">
              <p>Our goal at the Arasgrasa Society is to reconnect people with the ancient wisdom of nature. By harnessing the power of Arasgrasa and other sacred herbs, we aim to restore balance, vitality, and a sense of purpose in a fast-paced world. We believe that through this timeless elvish knowledge, we can create a future where wellness is rooted in harmony with the Earth.</p>
            </blockquote>
            <figcaption class="mt-8 text-base">
              <div class="font-semibold text-white">Judith Black</div>
              <div class="mt-1 text-gray-400">CEO of Arasgrasa Tech</div>
            </figcaption>
          </figure>
        </div>
      </div>
    </div>
  </div>
  <div class="jacquard-12-regular bg-slate-900 py-24 sm:py-32">
    <div class="mx-auto max-w-7xl px-6 lg:px-8">
      <div class="mx-auto max-w-2xl lg:mx-0">
        <h2 class="text-5xl font-bold tracking-tight text-white sm:text-4xl">Arasgrasa team</h2>
        <p class="mt-6 text-3xl leading-8 text-gray-200">We are a collective of herbalists, wellness advocates, and nature enthusiasts deeply committed to the healing power of Arasgrasa. United by our passion for holistic living, we strive to share the wisdom of nature through our herbal blends, empowering individuals to find balance and vitality in their everyday lives.</p>
      </div>
      <ul role="list" class="mx-auto mt-20 grid max-w-2xl grid-cols-2 gap-x-8 gap-y-16 text-center sm:grid-cols-3 md:grid-cols-4 lg:mx-0 lg:max-w-none lg:grid-cols-5 xl:grid-cols-6">
        <li v-for="person in people" :key="person.name">
          <img class="mx-auto h-24 w-24 rounded-full" :src="person.imageUrl" :alt="person.name" />
          <h3 class="mt-6 text-2xl font-semibold leading-7 tracking-tight text-white">{{ person.name }}</h3>
          <p class="text-xl leading-6 text-gray-200">{{ person.role }}</p>
        </li>
      </ul>
    </div>
  </div>
</template>

<script setup lang="ts">
const people = [
  {
    name: 'Michael Foster',
    role: 'Lead Developer',
    imageUrl: 'https://api.dicebear.com/9.x/micah/svg?seed=michaelfoster'
  },
  {
    name: 'Sara Johnson',
    role: 'Product Manager',
    imageUrl: 'https://api.dicebear.com/9.x/micah/svg?seed=sarajohnson'
  },
  {
    name: 'Alex Lee',
    role: 'Designer',
    imageUrl: 'https://api.dicebear.com/9.x/micah/svg?seed=alexlee'
  },
  {
    name: 'Emily White',
    role: 'Marketing Specialist',
    imageUrl: 'https://api.dicebear.com/9.x/micah/svg?seed=emilywhite'
  },
  {
    name: 'David Brown',
    role: 'Customer Support',
    imageUrl: 'https://api.dicebear.com/9.x/micah/svg?seed=davidbrown'
  },
  {
    name: 'Jessica Green',
    role: 'Content Writer',
    imageUrl: 'https://api.dicebear.com/9.x/micah/svg?seed=jessicagreen'
  },
  {
    name: 'Chris Taylor',
    role: 'SEO Specialist',
    imageUrl: 'https://api.dicebear.com/9.x/micah/svg?seed=christaylor'
  },
  {
    name: 'Sophia Martinez',
    role: 'HR Manager',
    imageUrl: 'https://api.dicebear.com/9.x/micah/svg?seed=sophiamartinez'
  },
  {
    name: 'Daniel Clark',
    role: 'Finance Manager',
    imageUrl: 'https://api.dicebear.com/9.x/micah/svg?seed=danielclark'
  },
  {
    name: 'Olivia Adams',
    role: 'Legal Advisor',
    imageUrl: 'https://api.dicebear.com/9.x/micah/svg?seed=oliviaadams'
  },
  {
    name: 'Ethan Wright',
    role: 'IT Specialist',
    imageUrl: 'https://api.dicebear.com/9.x/micah/svg?seed=ethanwright'
  },
  {
    name: 'Ava Hill',
    role: 'Office Manager',
    imageUrl: 'https://api.dicebear.com/9.x/micah/svg?seed=avahill'
  }
]

useHead({
  title: 'About Arasgrasa - Herbal Wisdom & Community',
  meta: [
    {
      name: 'description',
      content: 'Learn about the Arasgrasa Society, our mission, and the team behind our herbal blends. Discover the power of Arasgrasa and our commitment to holistic wellness.'
    },
    {
      name: 'keywords',
      content: 'Arasgrasa, herbal blends, natural energy, Arasgrasa Tech, about us, wellness, herbal tea, elvish herbal remedies'
    },
    {
      name: 'author',
      content: 'Arasgrasa Tech'
    }
  ]
})

</script>

<style scoped>
/* Add any custom styles if necessary */
</style>
