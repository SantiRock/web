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

    closeFunction();

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
    cursor: url('data:./cursor/circuloblanco.png;base64,iVBORw0KGgoAAAANSUhEUgAAAA4AAAAOCAMAAAAolt3jAAAAAXNSR0IB2cksfwAAAAlwSFlzAAALEwAACxMBAJqcGAAAAEVQTFRFAAAA5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfxp1coYwAAABd0Uk5TABOJvOyIFE3t/1BhF/f2GYPY1PjwuoZdf0L0AAAAVklEQVR4nF2PWQ6AIAwFH7LviOj9jyqikWW+OknTTAGAbJQxygUaUumGMo9Z/WMB57uGiKQHEvZRM45RC8qseV5eTsXQzbs1AzBfJJNvtOD1hfMidbwBky0GZz0ZqGgAAAAASUVORK5CYII=') 0 0, auto;
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
    cursor: url('data:./cursor/circulolineanegra.png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAMAAAAoLQ9TAAAAAXNSR0IB2cksfwAAAAlwSFlzAAALEwAACxMBAJqcGAAAAFFQTFRFAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAXKkVQgAAABt0Uk5TAAxEYlpjCxpcZlsYH2EcRWVdZENZChdgFhlCSBpx0QAAAGdJREFUeJxlj1kOgCAQQyswCK4guN7/oOISBHl/fWkyUwCoGBdEgjOJm1rpl6a9ctfrSD+EvtAJQmI0qTAMpDMIKhe2bBTC5kL9G9P/rIP0qfAzsKxfXrdrzB5fUcszVzpqwnw6Qh8nO2AIldRxrOgAAAAASUVORK5CYII=') 0 0, pointer;
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
    cursor: url('data:./cursor/circulonegro.png;base64,iVBORw0KGgoAAAANSUhEUgAAABQAAAAUCAMAAAC6V+0/AAAAAXNSR0IB2cksfwAAAAlwSFlzAAALEwAACxMBAJqcGAAAALdQTFRFAAAAqtjKos7Am8W4epyUY356nsi6os3Aq9fJpNvInci7cZCKGB8mAAALcpKMnsm8otHRktu2rdzMFBoiFx4lrt3OqtWqr97OmczMm8W4FBoiFx4lnMe6cI+Ic5OMqdfKo8/BGiEooczAmsS3nMa6eJmSepyTZH56ZIB6nci6n8m8oMy/GyMqoMy9cZGLdJONqtjJm8a5GSAnm8W5sN7PmczMdJSMdZWOnce6nMe6fJ6WY356n8q9Gh1AiAAAAD10Uk5TAGnb7ez57thnDsbx///xwgsH9/7++Qb5Csn9/cTz82Xa/9nu7/Dx+Pjv8dr/1vP0Y8X+wvsF8vLA7u368ILNhkAAAACiSURBVHicbdDXEoIwEAXQVUFREwWkWSn2ggJiA///uwxBGZNw33JmM5tcgCKNZkuSZandUeCXbq+PMA0aDNXSNH2EqximRed0zMR2CI4nLE5nZMccc1m44CEe/QCWvGG8grWIG9iKuKvH2ut7EQ9wFJ50CkE583iJAGKDteRK/q6aLKZaUZNl/80m6a0s1Inv/nfH46lV3bvBK8vz7B1G9PgB9OoX5Dj9cg0AAAAASUVORK5CYII=') 0 0, pointer;
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