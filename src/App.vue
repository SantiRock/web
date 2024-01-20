<script setup>
import Nav from './components/Nav.vue';
import Header from './components/Header.vue';
import Services from './components/Services.vue';
import Contact from './components/Contact.vue';
import Project from './components/Project.vue';
import About from './components/About.vue';
import Footer from './components/Footer.vue';

</script>

<template>
  <header>
    <Nav />
    <Header />
  </header>
  <main>
    <Services />
    <Contact />
    <Project />
    <About />
  </main>
  <Footer />
</template>

