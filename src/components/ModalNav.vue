<script setup>

const props = defineProps({
    close: Function,
    required: true
})

const closeFunction = () => { props.close()};

function scrollToSection(sectionId) {
  const section = document.getElementById(sectionId);

  if (section) {
    section.scrollIntoView({
      behavior: 'smooth', // Hace que el desplazamiento sea suave
    });

  }
}

const clickClose = evt => {
    if(evt.currentTarget === evt.target) {
        closeFunction();
    }
}


</script>

<template>
    <div class="container_m" @click="clickClose">
        <div class="container_modal">
        <button class="close_btn" @click="closeFunction">X</button>

        <div >
            <ul class="modal_menu">
                <li class="modal_link_container"><a class="modal_link" @click="scrollToSection('services')">Propuesta</a></li>
                <li class="modal_link_container"><a class="modal_link" @click="scrollToSection('contact')">Contacto</a></li>
                <li class="modal_link_container"><a class="modal_link" @click="scrollToSection('projects')">Proyectos</a></li>
                <li class="modal_link_container"><a class="modal_link" @click="scrollToSection('about')">Acerca</a></li>
            </ul>    
        </div>
    </div>
    </div>
</template>

<style>
.container_m {
    position: fixed;
    top:0;
    height: 100vh;
    width: 100vw;
    background-color: transparent;
    z-index: 7;
}

.container_modal {
    position: fixed;
    top:0;
    right: 0;
    height: 100vh;
    width: 268px;
    background-color: rgb(178, 226, 210);
    color: black;
    cursor: url('./circuloblanco.svg') 0 0, auto;
    z-index: 10;
}

.close_btn {
    margin-top: 13px;
    margin-left: 226px;
    margin-bottom: 7px;
    font-size: 33px;
    color: black;
    transition: transform 0.5s ease;
    width: 37px;
}

.close_btn:hover {
    transform: rotate(-270deg);
    color: white;
    cursor: url('./circulolineanegra.svg') 0 0, pointer;
}


.modal_menu {
    margin-left: 33px;
}

.modal_link_container {
    margin-bottom: 21px;
    width: fit-content;
}

.modal_link {
    display: inline-block;
    font-size: 33px;
}

.modal_link:hover {
    color: white;
    cursor: url('./circulonegro.svg') 0 0, pointer;
}

.modal_link_container:not(:hover) .modal_link {
    animation: slideup 200ms ease;
}

.modal_link_container:hover .modal_link {
    animation: slidedown 200ms ease;
}


@keyframes slidedown {
    0% {
        transform: translateY(20px);
    }
    100% {
        transform: translateY(0);
    }
}

@keyframes slideup {
    0% {
        transform: translateY(-20px);
    }
    100% {
        transform: translateY(0);
    }
}


</style>