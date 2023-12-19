<template>
  <div class="app">
    <nav class="flex items-center justify-between h-12 px-4">
      <div>
        <!-- Ici, tu peux ajouter un logo ou quelque chose de similaire -->
      </div>
      <div class="hidden md:flex">
        <router-link to="/" class="p-2">Home</router-link>
        <router-link to="/about" class="p-2">About</router-link>
      </div>
      <button @click="toggleMenu" class="md:hidden">☰</button>
    </nav>

    <div v-show="isMenuOpen" class="flex flex-col md:hidden">
      <router-link to="/" class="p-2 text-white">Home</router-link>
      <router-link to="/about" class="p-2 text-white">About</router-link>
    </div>

    <div class="page flex flex-grow items-center m-10">
      <router-view />
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const isMenuOpen = ref(false);

function toggleMenu() {
  isMenuOpen.value = !isMenuOpen.value;
}
</script>

<style lang="scss">
.app {
  @apply min-h-screen flex flex-col;
  background: -webkit-linear-gradient(35deg, #23379a, #09133c);
  background: linear-gradient(35deg, #23379a, #09133c);
}

nav {
  height: 50px;
  color: white;
}

.page {
  flex-grow: 1;
}
</style>
