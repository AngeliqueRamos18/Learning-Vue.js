<script setup>
// some of the references files from created project were used (_theme_files)
// In this part we are calling the Navbar.vue file to import to our main App 
import Navbar from '@/components/Navbar.vue'
import { RouterView } from 'vue-router';
</script>

<template>
  <Navbar />
  <!-- This will display all of the components created within the "HomeView.vue" file -->
  <RouterView />
</template>