<script setup>
import { ref } from 'vue';

const response = ref(false)
const si = ref(false)

function changeColor(isHover) {
    const tienesdiseno = document.querySelector('.tienes_diseno');
    tienesdiseno.style.color = isHover ? 'rgb(178, 226, 210)' : 'white';
    response.value = false
    si.value = false
}

function changeColorr(isHover) {
    const btns = document.querySelectorAll('.header_btn');

    btns.forEach(function(btn) {
        btn.style.color = isHover ? 'rgb(178, 226, 210)' : 'white';
    })

    response.value = false
    si.value = false
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


</script>

<template>
    <div class="containerh">
        <h1 class="titulo" @mouseout="changeColor(false)" @mouseover="changeColor(true)">¿Necesitas una página web?</h1>
       <div class="pregunta_container">
        <div class="tienes_diseno">
            <p class="pregunta" @mouseout="changeColorr(false)" @mouseover="changeColorr(true)">¿Tienes el diseño?</p>
            <div>
              <button class="header_btn" @mouseover="showSi">Si</button>
              /
              <button class="header_btn" @mouseover="showNo">No</button>
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
    cursor: url('data:./cursor/circulolineagrande.png;base64,iVBORw0KGgoAAAANSUhEUgAAAEAAAABACAMAAACdt4HsAAAAAXNSR0IB2cksfwAAAAlwSFlzAAALEwAACxMBAJqcGAAAAThQTFRFAAAAptnMsOLQsuHSseHRsuLSsuLSsuHRseLSsuLRseHRsuHQrtfJseDPsuHRseHRsuLRseHRst/RqtWqsOHSsuHSseHRseHSseHRgL+/seHQseLRseHSseHRseLSsOHSsd/RsuHSsuHSr+LQseHSseHRseHSrtzRsuHSseHRruDOr+HSr97QseHSseDQrt/OsN3SruDNsuLRseLRseHSseLSsuHRseLRsuLRr+DSsuHSseHRseHRgICAsuDRseHRseHSr9/Pr+DRsuHRsuLRsuHSsuLRseLRseHSseDQqt3MseLRseHSseLSseHRseLSseDQsuLRseLSsN/Qr+HRseLRsOHOrt3Qrt7OseLOseDQsuLRseHSseHRseHPsuDRseLQsODRsuLSseLQsuHRsuLSseHSseLSwmk9UAAAAGh0Uk5TAAgjPUxmX1phZDwiCCROVl5OJAI6WGBYOgI3ZWRkZTYdYGMcRF1BCVxcFxQWYRoZEhBXV1xaRWJCHV8zMAE1WU8GIT5QT2JQPSEGTSJYNjQyMV4cG0IRDxMVFFtCQBwaNDVMO0taSzs3jzwNAAACFElEQVR4nKWXa0PaMBSGz5CDZeJEHVEn1BWF2c1uCl42NkWdouJtXjadt111//8fLG1BoDQ0yXm+8KXP23CSJicAoTyJ9cUx0Z8wkkmD/2D86UAq/MlQBp8NpTFAemh4RM4efZ5hQduHjY1PRPsvJrPhukvOnIrQX1p5se6SZ9O9/JlCb92lUBTqr2YjXt8YhC2YkNe2jO5ivwnz5wxZH9EJSXjryPs84V3QnxfMvQhrIVC/kpqPWO6s5KKqj+ZSu7/cY/WJWHnf8j9Y6j4vQ2tNKhawSaXpf1RYAe0Yn3x/dFLP56x6AVMrun5+zQuoag8AM64/qDUFPlaMB6zr+4jDfP/NUAKqGxCrUALYJhQpPpqfYYsUgNtA8xGBMIkuFhRoAbOg+SE1MaBGC6hBkhaQpAeQ/wKxiAy6WhE1CtSFZNCX8g7NX4eiSQrYhQHNU8WH7UGKtqXVAbYpAft8Vx5Rak06cQ7cg2FMP+DQO5mOpJq7MPLHXsCE/kQ2jvcvmh9U7YTYYJw+dihnWgnWeatJmtFosrJf29s06Tb5kc42D1LKjWap3tmqflMsg3MBAS6VEth80Af4rrA/1666fYCFa1nf7hp/o5K23JVnqR7uc24kNvn0rVDn3FUiBpFN/Ojlc9YwJ9Zz+DNC56z+KgkOG6csoXvEfpe7L9/l+IGk7rKx+eevye796/89Mx/+7QlK/x+ms2VjULDcKAAAAABJRU5ErkJggg==') 0 0, auto;
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
    cursor: none;
    transition: background-color 250ms;
}

.header_btn:hover {
    background-color: var(--verde-claro);
}

.pregunta {
    cursor: none;
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
        cursor: url('data:./cursor/circulolineaultragrande.png;base64,iVBORw0KGgoAAAANSUhEUgAAAIAAAACACAMAAAD04JH5AAAAAXNSR0IB2cksfwAAAAlwSFlzAAALEwAACxMBAJqcGAAAAdpQTFRFAAAApNvIsuDRsODSseHRsuHRsuLSseLRseHSseLSseLRseHSsuLSsuHSsOHQsODRseDQsdjEpeHSseHRseHSseHRseHRsuLRseHRsuHRr9/PrdvRseHQsuHSseHSqtnQqqqqsuDRseLRseLSseLSsN/Qr97QseLRseHRseLOr9/PseHSseLRsd7SsODPsd/Rrd3PsuHRseHSr+HSseHSseLSsODRsuLRseDQptnMsuLSsuLRseHRsuHQr+DRsuHRsuLRsuHSsuHRqtXGseHRsOHRsuHSsODQsOHRsuHSsuLRsuDRseHSr+HQseHRseHRseDQseLRseDQseLRruDOqtvOsuLSseHRseLSsOLQseHRsuLSsuLRseDQr+LQsuLRsuLSruHQsuLRreDRseHSseHRqt/KsOHQsODRseHSqsbGmczMseLSseHRseLRmczMsOHQsuHSsuLRseHSseLSseLRsuHRseLQsuHSsOLRsuDQr+DSseHPn9+/gL+/sd7IsuLSseHRseDPseLRr9/PsODPseHRsOHSsuHSrt7OsuLSseHSsOHRseLRseHSr9/PsuLSseDPseLQsODSsOHSseLQsOHRsd7NseLRseLRsuLRsuHRseHRsuLRmiP+hwAAAJ50Uk5TAAYaK0BSX2VdYWJkZlJAKhoFB0hcZGBkXEcGCzdYWAsBKFRlVCcWRUQVGlFQGR4dFUtKFEFeKGInCExeTCIhQVtjWgddImAgLF84NWElNzYrKiEfFwhaWT8jTiZCFBxUUxhQFERSCjAuVQQCOzpXBCk9PE9aWz47KRg5HRwDAglRJiRDExdTG0oTPygmTSIgIB40JDYqHxI+SklDM1eFfSvpAAAEaElEQVR4nM2b50PTQBiHX4ZtE05QtKmzInELiihELCpBrUbrHigqKsOBeyFOcICKe+//1bQROkiaS3J3r88nPuX59cjdvbkB4JmS0rLyKaFwRJIkuYKQCtn8IxIOTa2smjbd+9M8Ul02Y2ZUiRFbYkp01uyqOfzsc+fNj8n27ixyOD5vAQ97zcJaOexmt1DlRYtZ65csVV1/e147kGXLGepXrFS82C2UunpG+lW1PvRpQotWM9A3rAn502ciNK4N6l/X5F+fiVAeSN9MtGB+83VU1/vWt2xIBNWnSbRW+/Nv1Cj7vRtheZMf/2YmP9+iqdKzvqVNZ+cnRG/f4s1fyvDnW2z1NCxtS7L2E5LcTu/fYbD3E2KU0fp3Bhj7ihHaRedvTvHxm/PTbhr/Hp9TD1WCve7+fZza38LY7+Y/wLz/5dN0sLj/EJf3PxeloZj/cIS3n5BIsbL5CH8/IR3O/vLAsz8N2lEn/zGuHSCL4TAotwj5/Wl0+9egUxUVQO208zdzHAELUY7bBBCnNwlP9p9gWgG5oU+q1hu4D4H5GCcLArSK9RPSmO9fJfANtAh15QU4JdpPyOlc/wrhDWB2xTM5AaaK9xPSnfUv4VCFu5PqmQiwFMNPSO+4v0bYJFDAeIDFKRx/crxK78PxT7yGcyWsANrZTIBzaAGk85kAF7D8hNSm/f1RvADhiyjzUBYlPSNdwvMT9bIZII4YgFwBKBFaihUSvQqlgr5G7DHqoQy1BfRrcB3TT8gNqMMNcBM4r4i4sRUctuBEocIt3ADtgDgQp1HwA6RwA6TA034keyRAHQjNqgy7G8bwAwhbGrNHA7SS2AK9G/4HAxF6AOTJ6DYw2h/2DXZBEoFu3ACdMIAb4A5Uoc5GFYMwDffD5C5Mr8AMEOvH/ziFS1iLdGnumQHuoyyTWigPzAAPEUsS9dH/sEiFuEynWct0C9CqMm3IWiqdghVg+N9a8WOkfpB6Mr5cjuPPLtdDL47/6USA5SkMv/Qsu2k0jBGgLmfXrB5j224kd+OwVnyA0Vw/rBbeBMbzvADiN69f5PthreAmUF4WBIDNYg8wjBX6AYQWRrHJfngl8hDLa5sA8EZcgFY7P1QLewt0h7sob0Ud5Xpn7wcYE1IbyQNOfoAOEQHizn7Y0sbf31ZSJAA0cO+LycITTAW857xiEvpQ3A9QxfVMlzLo5gfYy/G/kPzo7gd4neLllz7R+AE+c2oDg/JwO6/j/coXWj/AOw7fStJXej9AD/PemPjmxQ8wp53tJZeOouOfLWMBL3nlEvruWW9yQGd10Ul/78dv/htamTRCU6P/u7DHw4H3NeWobf1HTWXAKslwPEpPy8kfAUYl5eek7w8fdI36jKD0PXd/OhVnbvoYGZOdI+5Ppqanl3i89vvrmftTvfF4VKf8elP1PqorVZ45+/uP+/VnWf3ze4iLPsPFrhvxWNLx8nssfufBI372f1ytv/Z9OKFGJEmzrv9rkhQhie6Bwbv93p/2F907yFq7waZvAAAAAElFTkSuQmCC') 0 0, auto;
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