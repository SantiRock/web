<script setup>
import { ref, onMounted } from 'vue';
import Nav from './components/Nav.vue';
import Header from './components/Header.vue';
import Services from './components/Services.vue';
import Contact from './components/Contact.vue';
import Project from './components/Project.vue';
import About from './components/About.vue';
import Footer from './components/Footer.vue';
import Lng from './components/Lng.vue';
import { contentapi } from './components/content';

let api = ref(contentapi.es)

onMounted(() => {
  if (navigator.language.startsWith('es')) {
    api.value = contentapi.es
  } else {
    api.value = contentapi.en
  }
})

</script>

<template>
  <header>
    <Lng @lng="(obj) => api = obj"/>
    <Nav  :obj="api" />
    <Header :obj="api"/>
  </header>
  <main>
    <Services :obj="api"/>
    <Contact :obj="api"/>
    <Project :obj="api" />
    <About :obj="api"/>
  </main>
  <Footer :obj="api"/>
</template>

