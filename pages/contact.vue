<script setup lang="ts">

useHead({
  title: 'Contact the Arasgrasa Tech - Herbal Wisdom & Community',
  meta: [
    {
      name: 'description',
      content: 'Connect with the Arasgrasa Tech. Discover the power of Arasgrasa, our herbal blends, and events. Contact us for inquiries, support, or collaboration.'
    },
    {
      name: 'keywords',
      content: 'Arasgrasa, herbal blends, natural energy, Arasgrasa Tech, contact, wellness, herbal tea, elvish herbal remedies'
    },
    {
      name: 'author',
      content: 'Arasgrasa Tech'
    }
  ]
})

</script>

<template>
  <div class="bg-slate-900 py-24 sm:py-32 jacquard-12-regular">
    <div class="mx-auto max-w-7xl px-6 lg:px-8">
      <div class="mx-auto max-w-2xl lg:mx-0">
        <h2 class="text-5xl font-bold tracking-tight text-green-600">
          Connect with the Arasgrasa Society
        </h2>
        <p class="mt-6 text-2xl leading-8 text-gray-300">
          We value our connection with the community. Whether you have questions
          about our herbal blends, events, or want to explore the healing powers
          of Arasgrasa, feel free to reach out to us.
        </p>
      </div>

      <!-- Office Locations -->
      <div class="mx-auto mt-16 grid max-w-2xl grid-cols-1 gap-8 text-base leading-7 sm:grid-cols-2 sm:gap-y-16 lg:mx-0 lg:max-w-none lg:grid-cols-4">
        <div>
          <h3 class="border-l text-3xl border-green-600 pl-6 font-semibold text-white">Elvenwood (HQ)</h3>
          <address class="border-l text-xl border-gray-200 pl-6 pt-2 not-italic text-gray-200">
            <p>123 Arasgrasa Grove</p>
            <p>Elvenwood, EA 56789</p>
            <p>Email: contact@arasgrasa.org</p>
          </address>
        </div>
        <div>
          <h3 class="border-l text-3xl border-green-600 pl-6 font-semibold text-white">Los Angeles</h3>
          <address class="border-l text-xl border-gray-200 pl-6 pt-2 not-italic text-gray-200">
            <p>4556 Brendan Ferry</p>
            <p>Los Angeles, CA 90210</p>
            <p>Email: la-office@arasgrasa.org</p>
          </address>
        </div>
        <div>
          <h3 class="border-l text-3xl border-green-600 pl-6 font-semibold text-white">New York</h3>
          <address class="border-l text-xl border-gray-200 pl-6 pt-2 not-italic text-gray-200">
            <p>886 Walter Street</p>
            <p>New York, NY 12345</p>
            <p>Email: ny-office@arasgrasa.org</p>
          </address>
        </div>
        <div>
          <h3 class="border-l text-3xl border-green-600 pl-6 font-semibold text-white">Toronto</h3>
          <address class="border-l text-xl border-gray-200 pl-6 pt-2 not-italic text-gray-200">
            <p>7363 Cynthia Pass</p>
            <p>Toronto, ON N3Y 4H8</p>
            <p>Email: toronto-office@arasgrasa.org</p>
          </address>
        </div>
      </div>

      <!-- Contact Form -->
      <div class="mt-16">
        <h2 class="text-5xl font-bold tracking-tight text-green-600">Get in Touch</h2>
        <p class="mt-4 text-2xl leading-8 text-gray-200">
          Have questions or want to learn more about the benefits of Arasgrasa? Fill out
          the form below, and our team will get back to you shortly.
        </p>
        <form class="mt-8 max-w-3xl space-y-6">
          <div>
            <label for="name" class="block text-xl font-medium text-white">Full Name</label>
            <input type="text" id="name" class="bg-slate-800 mt-1 block w-full px-4 py-3 border border-slate-600 rounded-md text-white placeholder-gray-400 shadow-sm focus:ring-green-500 focus:border-green-500" placeholder="Your name" />
          </div>
          <div>
            <label for="email" class="block text-xl font-medium text-white">Email Address</label>
            <input type="email" id="email" class="bg-slate-800 mt-1 block w-full px-4 py-3 border border-slate-600 rounded-md text-white placeholder-gray-400 shadow-sm focus:ring-green-500 focus:border-green-500" placeholder="you@example.com" />
          </div>
          <div>
            <label for="message" class="block text-xl font-medium text-white">Message</label>
            <textarea id="message" rows="4" class="bg-slate-800 mt-1 block w-full px-4 py-3 border border-slate-600 rounded-md text-white placeholder-gray-400 shadow-sm focus:ring-green-500 focus:border-green-500" placeholder="How can we help?"></textarea>
          </div>
          <div>
            <button type="submit" class="w-full px-4 py-3 text-white text-3xl bg-green-600 rounded-md shadow-sm hover:bg-green-700 focus:ring-4 focus:ring-green-300">Submit</button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<style scoped>
</style>
