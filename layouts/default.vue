<script setup lang="ts">

import NavBar from "~/components/NavBar.vue";
import Footer from "~/components/Footer.vue";

</script>

<template>
  <div>
    <nav-bar/>
    <slot/>
    <Footer/>
  </div>
</template>

<style scoped>

</style>
