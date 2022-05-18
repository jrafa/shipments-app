<script setup lang="ts">
import { RouterLink, RouterView } from "vue-router";
import Shipment from "@/components/Shipment.vue";
</script>

<template>
  <header>
    <div class="wrapper">
      <Shipment/>
      <nav>
        <RouterLink to="/">Shipments</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style>
@import "@/assets/base.css";

#app {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;

  font-weight: normal;
}

header {
  line-height: 1.5;
  max-height: 100vh;
}
a {
  text-decoration: none;
  color: hsla(160, 100%, 37%, 1);
  transition: 0.4s;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}
</style>
