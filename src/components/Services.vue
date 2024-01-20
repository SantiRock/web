<script setup>
import { ref } from 'vue';
const text = ref(false)

function servicesColor(isHover) {
    var items = document.querySelectorAll('.services_item');

    items.forEach(function(item) {
        item.style.color = isHover ? 'rgb(178, 226, 210)' : 'white';
    })
}

function showPixelPerfect() {
    text.value = true

    setTimeout(function () {
        const respuestaElement = document.querySelector('.services_text');
        respuestaElement.textContent = "Pixel Perfect, podemos trabajar en el diseño juntos, ya sea que tengas una idea, quieras algo clásico o tengas ganas de explorar posibilidades."
        }, 1);
}

function showResponsive() {
    text.value = true

    setTimeout(function () {
        const respuestaElement = document.querySelector('.services_text');
        respuestaElement.textContent = "Responsive, podemos trabajar en el diseño juntos, ya sea que tengas una idea, quieras algo clásico o tengas ganas de explorar posibilidades."
        }, 1);
}

function showAPI() {
    text.value = true

    setTimeout(function () {
        const respuestaElement = document.querySelector('.services_text');
        respuestaElement.textContent = "API, podemos trabajar en el diseño juntos, ya sea que tengas una idea, quieras algo clásico o tengas ganas de explorar posibilidades."
        }, 1);
}

function textHide() {
    text.value = false
}

</script>

<template>
    <div class="services_background">
        <div id="services" class="services_container">
            <h2 class="services_title" @mouseout="servicesColor(false)" @mouseover="servicesColor(true)">Lo que podemos ofrecerte</h2>
            <ul class="services_list">
                <li class="services_item" @mouseover="showPixelPerfect" @mouseout="textHide">Pixel Perfect</li>
                <li class="services_item" @mouseover="showResponsive" @mouseout="textHide">Responsive</li>
                <li class="services_item" @mouseover="showAPI" @mouseout="textHide">API</li>
            </ul>
            <Transition>
                <p v-if="text" class="services_text">No te preocupes, podemos trabajar en el diseño juntos, ya sea que tengas una idea, quieras algo clásico o tengas ganas de explorar posibilidades.</p>
            </Transition>
        </div>
        <div class="linea_container"><div class="linea"></div></div>
        
    </div>
</template>

<style>

.services_container {
    margin: auto; 
    margin-bottom: 10px;
    padding: 21px 35px;
    max-width: 1280px;
    min-width: 360px;
}

.services_title {
    width: 150px;
    font-size: 32px;
    font-style: italic;
    font-weight: lighter;
    cursor: url('./circulolinea.svg') 0 0, pointer;
}

.services_list {
    margin-left: auto;
    width: 120px;
}

.services_item {
    font-size: 18px;
    margin-bottom: 13px;
    cursor: url('./circulotransparente.svg') 0 0, pointer;
    
}

.services_item:hover {
    background-color: var(--verde-claro);
}

.services_text {
    width: 288px;
    font-size: 15px;
    line-height: 2.0;
    color: var(--verde-claro);
}

/* Estilo de transición */
.v-enter-active, .v-leave-active {
  transition: opacity 0.5s ease;
}
.v-enter-from, .v-leave-to {
  opacity: 0;
}

/* Responsive */

@media screen and (min-width: 700px) {
    .services_container {
        display: flex;
        padding-left: 45px;
    }

    .services_list {
        margin-left: 5vw;
        padding-top: 6px;
    }

    .services_text {
        margin-left: 5vw;
    }

    .services_title {
        font-size: clamp(32px, 5.5vw, 64px );
        width: 22vw;
    }
}

@media screen and (min-width: 900px) {
    .services_container {
        padding-left: 73px;
    }

    .services_title {
        cursor: url('./circulolineagrande.svg') 0 0, pointer;
    }
    
}

@media screen and (min-width: 1440px){
    .services_list {
        padding-top: 33px;
    }

    .services_text {
        padding-top: 27px;
    }
    
}


</style>