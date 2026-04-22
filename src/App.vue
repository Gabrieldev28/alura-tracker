<script setup lang="ts">
import SideBar from './components/SideBar.vue';
import Formulario from './components/Formulario.vue';

</script>

<template>
  <main class="w-full flex">
    <div class="w-1/4 ">
      <SideBar />
    </div>
    <div class="w-3/4 bg-blue-200">
      <Formulario />
    </div>
  </main>
</template>

<style scoped></style>
