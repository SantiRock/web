<script setup>
import { ref } from 'vue';
const text = ref(false)
const pp = ref(false)

function servicesColor(isHover) {
    var items = document.querySelectorAll('.services_item');

    items.forEach(function(item) {
        item.style.color = isHover ? 'rgb(178, 226, 210)' : 'white';
    })

    text.value = false
    pp.value = false


}

function showPixelPerfect() {
    text.value = true
    pp.value = true

    setTimeout(function () {
        const respuestaElement = document.querySelector('.services_text');
        respuestaElement.textContent = "Es nuestra capacidad para que tu sitio web se vea y funcione exactamente igual a como se planteó en el diseño original. Algunos ejemplos:"
        }, 1);
}

function showResponsive() {
    text.value = true
    pp.value = false

    setTimeout(function () {
        const respuestaElement = document.querySelector('.services_text');
        respuestaElement.textContent = "Tu sitio web se va a ver bien en cualquier tipo de pantalla y/o dispositivo adaptándose a sus medidas, ya sea un móvil, una tablet o un monitor de escritorio."
        }, 1);
}

function showAPI() {
    text.value = true
    pp.value = false

    setTimeout(function () {
        const respuestaElement = document.querySelector('.services_text');
        respuestaElement.textContent = "'Interfaz de programación de aplicaciones', aunque suene un poco abstracto, para simplificar, es la posibilidad de organizar, documentar la información que deseas compartir en una estructura de datos que la hace versátil y re-utilisable para proyectos web. Ya sea que quieras generar modificaciones al diseño o abrir una página nueva, no necesitas rehacerlo todo desde 0. Puedes adaptar la información al diseño que desees, cuando lo desees. "
        }, 1);
}


</script>

<template>
        <div id="services" class="services_container">
            <h2 class="services_title" @mouseout="servicesColor(false)" @mouseover="servicesColor(true)">Lo que podemos ofrecerte</h2>
            <ul class="services_list">
                <li class="services_item" @mouseover="showPixelPerfect" >Pixel Perfect</li>
                <li class="services_item" @mouseover="showResponsive" >Responsive</li>
                <li class="services_item" @mouseover="showAPI">API</li>
            </ul>
            <Transition>
                <div>
                    <p v-if="text" class="services_text"></p>
                    <ul v-if="pp" class="pp_links">
                      <li class="pp_linkc"><a href="https://www.frontendmentor.io/solutions/newsletter-signup-form-with-success-message-jOldFwfrVm" target="_blank" class="pp_link">Newsletter sign in</a></li>
                      <li class="pp_linkc"><a href="https://www.frontendmentor.io/solutions/nft-preview-card-component-pixel-perfect-BVV4CrKv-V" target="_blank" class="pp_link">NFT preview card</a></li>
                      <li class="pp_linkc"><a href="https://www.frontendmentor.io/solutions/frontend-mentor-qr-code-component-JMhaun5rjA" target="_blank" class="pp_link">Qr code component</a></li>
                    </ul>
                </div>
            </Transition>
        </div>
        <div class="linea_container"><div class="linea"></div></div>
        
</template>

<style>

.services_container {
    margin: auto; 
    margin-bottom: 10px;
    padding: 21px 35px;
    max-width: 1280px;
    min-width: 320px;
}

.services_title {
    width: 150px;
    font-size: 32px;
    font-style: italic;
    font-weight: lighter;
    cursor: url('data:./cursor/circulolinea.png;base64,iVBORw0KGgoAAAANSUhEUgAAABQAAAAUCAMAAAC6V+0/AAAAAXNSR0IB2cksfwAAAAlwSFlzAAALEwAACxMBAJqcGAAAAGlQTFRFAAAAseLRseLSsuLSseLSseHSsuHSseHRsOHQpNvIsuHSsuHSsuLSseHRotHRktu2suHSqtWqmczMsuLRseLSseLSseHSsuLRseLRseHRsuHSsuLRsuDRseHSsuLRmczMseHSsuLSseHRyrOKtAAAACN0Uk5TACpYX15kX1YpBk9gZk4EA2MCBFBlYShXV2BWYihPZAJhTWSrrDvsAAAAh0lEQVR4nG3Q6RaCIBQE4CmELK6Ca2Jq5vs/ZLh1Ypl/fAcO9w6w5nJlCeeJuKU4c39IOiKzfDel6S+82O45ZrW0WNUu1pn9oyEvTYunb0QdRIgGJkQJHaKOY/R5FCMj9UiD4V8DMPpo10TOXZvUWlPh6PTeCy3H+aT5o37dt51gy8JMP2zHL8u1EeCxPg+TAAAAAElFTkSuQmCC') 0 0, auto;
}

.services_list {
    margin-left: auto;
    width: 120px;
}

.services_item {
    font-size: 18px;
    margin-bottom: 13px;
    cursor: none;
    
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

.pp_links {
    margin-top: 13px;
    
}

.pp_link {
    color: white;
    text-decoration: none;
    cursor: url('data:./cursor/circulopeke.png;base64,iVBORw0KGgoAAAANSUhEUgAAAAUAAAAFBAMAAAB/QTvWAAAAAXNSR0IB2cksfwAAAAlwSFlzAAALEwAACxMBAJqcGAAAAA9QTFRFsuLSsuLSsuLSsuLSsuLSLoMBBAAAAAV0Uk5TG7TwvP+X/QQGAAAAF0lEQVR4nGNgVGRgMHExYFBxUQDTQD4AFToCHQBzmSoAAAAASUVORK5CYII=') 0 0, pointer;
}

.pp_link:hover {
    color: var(--verde-claro);
}

.pp_linkc {
    margin-bottom: 11px;
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

    .pp_links {
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
        cursor: url('data:./cursor/circulolineagrande.png;base64,iVBORw0KGgoAAAANSUhEUgAAAEAAAABACAMAAACdt4HsAAAAAXNSR0IB2cksfwAAAAlwSFlzAAALEwAACxMBAJqcGAAAAThQTFRFAAAAptnMsOLQsuHSseHRsuLSsuLSsuHRseLSsuLRseHRsuHQrtfJseDPsuHRseHRsuLRseHRst/RqtWqsOHSsuHSseHRseHSseHRgL+/seHQseLRseHSseHRseLSsOHSsd/RsuHSsuHSr+LQseHSseHRseHSrtzRsuHSseHRruDOr+HSr97QseHSseDQrt/OsN3SruDNsuLRseLRseHSseLSsuHRseLRsuLRr+DSsuHSseHRseHRgICAsuDRseHRseHSr9/Pr+DRsuHRsuLRsuHSsuLRseLRseHSseDQqt3MseLRseHSseLSseHRseLSseDQsuLRseLSsN/Qr+HRseLRsOHOrt3Qrt7OseLOseDQsuLRseHSseHRseHPsuDRseLQsODRsuLSseLQsuHRsuLSseHSseLSwmk9UAAAAGh0Uk5TAAgjPUxmX1phZDwiCCROVl5OJAI6WGBYOgI3ZWRkZTYdYGMcRF1BCVxcFxQWYRoZEhBXV1xaRWJCHV8zMAE1WU8GIT5QT2JQPSEGTSJYNjQyMV4cG0IRDxMVFFtCQBwaNDVMO0taSzs3jzwNAAACFElEQVR4nKWXa0PaMBSGz5CDZeJEHVEn1BWF2c1uCl42NkWdouJtXjadt111//8fLG1BoDQ0yXm+8KXP23CSJicAoTyJ9cUx0Z8wkkmD/2D86UAq/MlQBp8NpTFAemh4RM4efZ5hQduHjY1PRPsvJrPhukvOnIrQX1p5se6SZ9O9/JlCb92lUBTqr2YjXt8YhC2YkNe2jO5ivwnz5wxZH9EJSXjryPs84V3QnxfMvQhrIVC/kpqPWO6s5KKqj+ZSu7/cY/WJWHnf8j9Y6j4vQ2tNKhawSaXpf1RYAe0Yn3x/dFLP56x6AVMrun5+zQuoag8AM64/qDUFPlaMB6zr+4jDfP/NUAKqGxCrUALYJhQpPpqfYYsUgNtA8xGBMIkuFhRoAbOg+SE1MaBGC6hBkhaQpAeQ/wKxiAy6WhE1CtSFZNCX8g7NX4eiSQrYhQHNU8WH7UGKtqXVAbYpAft8Vx5Rak06cQ7cg2FMP+DQO5mOpJq7MPLHXsCE/kQ2jvcvmh9U7YTYYJw+dihnWgnWeatJmtFosrJf29s06Tb5kc42D1LKjWap3tmqflMsg3MBAS6VEth80Af4rrA/1666fYCFa1nf7hp/o5K23JVnqR7uc24kNvn0rVDn3FUiBpFN/Ojlc9YwJ9Zz+DNC56z+KgkOG6csoXvEfpe7L9/l+IGk7rKx+eevye796/89Mx/+7QlK/x+ms2VjULDcKAAAAABJRU5ErkJggg==') 0 0, auto;
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