<script setup>
import { ref } from 'vue'
import ModalNav from './ModalNav.vue';

const modal = ref(false)

function openModal() {
    modal.value = true
}

function closeModel() {
    modal.value = false
}

function scrollToSection(sectionId) {
  const section = document.getElementById(sectionId);

  if (section) {
    section.scrollIntoView({
      behavior: 'smooth', // Hace que el desplazamiento sea suave
    });
  }
}

</script>

<template>
    <nav class="container">
        <div class="mobile">
            <button class="mobile_menu" @click="openModal"></button>
        </div>

        <div >
            <ul class="nav">
                <li class="linkcontainer"><a class="link" @click="scrollToSection('services')">Propuesta</a></li>
                <li class="linkcontainer"><a class="link" @click="scrollToSection('contact')">Contacto</a></li>
                <li class="linkcontainer"><a class="link" @click="scrollToSection('projects')">Proyectos</a></li>
                <li class="linkcontainer"><a class="link" @click="scrollToSection('about')">Acerca</a></li>
            </ul>
        </div>

        <ModalNav v-if="modal" :close="closeModel"/>

    </nav >

</template>

<style>
.container {
    margin: auto;
    max-width: 1280px;
    min-width: 320px;
    margin-bottom: 37px;
}

.mobile {
    position: fixed;
    top: 18px;
    right: 16px;
    margin-left: auto;
    width: fit-content;
    z-index: 5;
}

.mobile_menu {
    width: 24px;
    height: 24px;
    border: 2px solid var(--verde-claro);
    background-color: rgb(19, 19, 19);;
    transition: transform 0.5s ease, background-color 0.5s ease;
    cursor: url('data:./cursor/circuloblanco.png;base64,iVBORw0KGgoAAAANSUhEUgAAAA4AAAAOCAMAAAAolt3jAAAAAXNSR0IB2cksfwAAAAlwSFlzAAALEwAACxMBAJqcGAAAAEVQTFRFAAAA5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfxp1coYwAAABd0Uk5TABOJvOyIFE3t/1BhF/f2GYPY1PjwuoZdf0L0AAAAVklEQVR4nF2PWQ6AIAwFH7LviOj9jyqikWW+OknTTAGAbJQxygUaUumGMo9Z/WMB57uGiKQHEvZRM45RC8qseV5eTsXQzbs1AzBfJJNvtOD1hfMidbwBky0GZz0ZqGgAAAAASUVORK5CYII=') 0 0, pointer;
}

.mobile_menu:hover {
    background-color: var(--verde-claro);
    transform: rotate(-90deg);
}

@media screen and (min-width: 641px) {
    .mobile {
        display: none;
    }

    .container {
        margin-bottom: 0;
    }
}

.nav {
    padding: 13px 0;
    padding-right: 33px;
    display: flex;
    justify-content: end;
    gap: 7%;
    animation: navmov 250ms ease;
    transform-origin: center right;
}

.link {
    font-size: 18px;
    color: var(--verde-claro);
    transition: color 0.75s ease;
    display: inline-block;
    cursor: url('data:./cursor/circulolinea.png;base64,iVBORw0KGgoAAAANSUhEUgAAABQAAAAUCAMAAAC6V+0/AAAAAXNSR0IB2cksfwAAAAlwSFlzAAALEwAACxMBAJqcGAAAAGlQTFRFAAAAseLRseLSsuLSseLSseHSsuHSseHRsOHQpNvIsuHSsuHSsuLSseHRotHRktu2suHSqtWqmczMsuLRseLSseLSseHSsuLRseLRseHRsuHSsuLRsuDRseHSsuLRmczMseHSsuLSseHRyrOKtAAAACN0Uk5TACpYX15kX1YpBk9gZk4EA2MCBFBlYShXV2BWYihPZAJhTWSrrDvsAAAAh0lEQVR4nG3Q6RaCIBQE4CmELK6Ca2Jq5vs/ZLh1Ypl/fAcO9w6w5nJlCeeJuKU4c39IOiKzfDel6S+82O45ZrW0WNUu1pn9oyEvTYunb0QdRIgGJkQJHaKOY/R5FCMj9UiD4V8DMPpo10TOXZvUWlPh6PTeCy3H+aT5o37dt51gy8JMP2zHL8u1EeCxPg+TAAAAAElFTkSuQmCC'), pointer;
    text-decoration: none;
}

.link:hover {
    color: white;
    animation-iteration-count: 1;
}

@media screen and (max-width: 640px) {
    .nav{
        display: none;
    }  
}

@media screen and (min-width: 700px) {

    
    .nav{
        margin-bottom: 21px;
    }  
}


@keyframes navmov {
  0% {
    transform: scaleX(0);
  }
  100% {
    transform: scaleX(1);
  }
}


</style>