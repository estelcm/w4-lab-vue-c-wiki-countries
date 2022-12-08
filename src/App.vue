<template>
  <div class="app">
    <Navbar />
    <Countries />
    <router-view />
  </div>
</template>

<script>
import Navbar from "./components/Navbar.vue";
import Countries from "../public/countries.json";
export default {
  components: { Navbar, Countries }
}
</script>

<style>

</style>