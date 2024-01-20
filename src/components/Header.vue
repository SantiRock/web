<script setup>
import { ref } from 'vue';

const response = ref(false)
const si = ref(false)

function changeColor(isHover) {
    const tienesdiseno = document.querySelector('.tienes_diseno');
    tienesdiseno.style.color = isHover ? 'rgb(178, 226, 210)' : 'white';
}

function changeColorr(isHover) {
    const btns = document.querySelectorAll('.header_btn');

    btns.forEach(function(btn) {
        btn.style.color = isHover ? 'rgb(178, 226, 210)' : 'white';
    })
}

function showSi() {
    response.value = true
    si.value = true

    setTimeout(function () {
        const respuestaElement = document.querySelector('.respuesta');
        respuestaElement.textContent = "Pixel Perfect podemos lograr que tu web quede exactamente igual a tu diseño. Acá algunos ejemplos:"
        }, 1);
}

function showNo() {
    response.value = true
    si.value = false

setTimeout(function () {
    const respuestaElement = document.querySelector('.respuesta');
    respuestaElement.textContent = "No te preocupes, podemos trabajar en el diseño juntos, ya sea que tengas una idea, quieras algo clásico o tengas ganas de explorar posibilidades."
    }, 1); 
}

function hide() {
    response.value = false
    si.value = false
}

</script>

<template>
    <div class="containerh">
        <h1 class="titulo" @mouseout="changeColor(false)" @mouseover="changeColor(true)">¿Necesitas una página web?</h1>
       <div class="pregunta_container">
        <div class="tienes_diseno">
            <p class="pregunta" @mouseout="changeColorr(false)" @mouseover="changeColorr(true)">¿Tienes el diseño?</p>
            <div>
              <button class="header_btn" @mouseover="showSi" @click="hide">Si</button>
              /
              <button class="header_btn" @mouseover="showNo" @click="hide">No</button>
            </div>
        </div>
        <Transition>
            <div>
                <p v-if="response" class="respuesta"></p>
                <ul v-if="si" class="si_links">
                    <li class="pp_linkc"><a href="https://www.frontendmentor.io/solutions/newsletter-signup-form-with-success-message-jOldFwfrVm" target="_blank" class="pp_link">Newsletter sign in</a></li>
                    <li class="pp_linkc"><a href="https://www.frontendmentor.io/solutions/nft-preview-card-component-pixel-perfect-BVV4CrKv-V" target="_blank" class="pp_link">NFT preview card</a></li>
                    <li class="pp_linkc"><a href="https://www.frontendmentor.io/solutions/frontend-mentor-qr-code-component-JMhaun5rjA" target="_blank" class="pp_link">Qr code component</a></li>
                </ul>
            </div>
            
        </Transition> 
       </div>
    </div>
    <div class="linea_container"><div class="linea"></div>  </div>
     
</template>

<style>
.containerh {
    margin: auto;
    padding: 0 35px;
    margin-bottom: 33px;
    max-width: 1280px;
    min-width: 320px;
}

.titulo {
    margin-bottom: 27px;
    font-size: clamp(48px, 13vw, 96px);
    width: 68vw;
    min-width: 245px;
    max-width: 514px;
    font-style: italic;
    font-weight: lighter;
    cursor: url('./circulolineagrande.svg') 0 0, pointer;
}

.tienes_diseno {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 230px;
    margin-bottom: 13px;
}

.header_btn {
    padding: 9px 0;
    width: 37px;
    border-radius: 50%;
    cursor: url('./circulotransparente.svg') 0 0, pointer;
    transition: background-color 250ms;
}

.header_btn:hover {
    background-color: var(--verde-claro);
}

.pregunta {
    cursor: url('./circulotransparente.svg') 0 0, pointer;
}

.respuesta {
    max-width: 320px;
    font-size: 15px;
    line-height: 2.0;
    color: var(--verde-claro);
}

.linea_container {
    margin: auto;
    padding: 0 21px;
    max-width: 1280px; 
}

.linea {
    border: 1px solid grey;
}

.si_links {
    margin-top: 13px;
}

/* Estilo de transición */
.v-enter-active, .v-leave-active {
  transition: opacity 0.5s ease;
}
.v-enter-from, .v-leave-to {
  opacity: 0;
}

@media screen and (min-width: 500px) {
    .pregunta_container {
        padding-left: 35vw;
    }  
    .titulo {
        margin-bottom: 0;
    }
}

@media screen and (min-width: 580px) {
    .pregunta_container {
        padding-left: 40vw;
    }
    
}

@media screen and (min-width: 800px) {
    .titulo {
        margin-left: 33px;
    }
    
    .pregunta_container {
        padding-left: 50vw;
    }  
}

@media screen and (min-width: 900px) {
    .containerh {
        display: flex;
    }

    .titulo {
        cursor: url('./circulolineaultragrande.svg') 0 0, pointer;
    }

    .pregunta_container {
        padding-top: 51px;
        padding-left: 3vw;
    }

    .linea {
        border: none;
    }
}


@media screen and (min-width: 1023px) {
    .pregunta_container {
        padding-top: 51px;
        padding-left: 7vw;
    }

    
}


</style>