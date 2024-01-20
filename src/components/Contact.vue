<script setup>
import { ref } from 'vue';

const emailMsn = ref(false)
const msn = ref('Dale click al correo para copiarlo')

function contactColor(isHover) {
    const email = document.querySelector('.contact_email');
    email.style.color = isHover ? 'rgb(178, 226, 210)' : 'white';
}

function showMsn() {
    contactColor(true);
    emailMsn.value = true
}

function hideMsn() {
    contactColor(false);
    emailMsn.value = false;
}

function showMsnEmail() {
    emailMsn.value = true
    const email = document.querySelector('.contact_email');
    email.style.backgroundColor = "#76AC89";
}

function hideMsnEmail() {
    emailMsn.value = false;
    const email = document.querySelector('.contact_email');
    email.style.backgroundColor = "transparent";
} 

const copyEmail = () => {
    const textToCopy = 'sqp.dev@gmail.com';
    navigator.clipboard.writeText(textToCopy);
    msn.value = "El correo ha sido copiado";
    const email = document.querySelector('.contact_email');
    email.style.backgroundColor = "white";

    setTimeout(() => {
        email.style.backgroundColor = "transparent"
    }, 100)

    setTimeout(() => {
        msn.value = "Dale click al correo para copiarlo"
        
    }, 2500);
  }

</script>

<template>
    <div class="contact_container" id="contact">
        <h2 class="contact_title" @mouseout="hideMsn" @mouseover="showMsn">Cuentanos sobre tu proyecto</h2>
        <p class="contact_email" @mouseout="hideMsnEmail" @mouseover="showMsnEmail" @click="copyEmail">sqp.dev@gmail.com</p>
        <p v-if="emailMsn" class="email_msn">{{ msn }}</p>
    </div>
    <div class="linea_container"><div class="linea"></div></div>
</template>

<style>

.contact_container {
    margin: auto; 
    margin-bottom: 7px;
    padding: 21px 35px;
    max-width: 1280px;
    min-width: 320px;
}

.contact_title {
    width: 170px;
    font-size: 22px;
    font-style: italic;
    font-weight: lighter;
    cursor: url('data:./cursor/circulolinea.png;base64,iVBORw0KGgoAAAANSUhEUgAAABQAAAAUCAMAAAC6V+0/AAAAAXNSR0IB2cksfwAAAAlwSFlzAAALEwAACxMBAJqcGAAAAGlQTFRFAAAAseLRseLSsuLSseLSseHSsuHSseHRsOHQpNvIsuHSsuHSsuLSseHRotHRktu2suHSqtWqmczMsuLRseLSseLSseHSsuLRseLRseHRsuHSsuLRsuDRseHSsuLRmczMseHSsuLSseHRyrOKtAAAACN0Uk5TACpYX15kX1YpBk9gZk4EA2MCBFBlYShXV2BWYihPZAJhTWSrrDvsAAAAh0lEQVR4nG3Q6RaCIBQE4CmELK6Ca2Jq5vs/ZLh1Ypl/fAcO9w6w5nJlCeeJuKU4c39IOiKzfDel6S+82O45ZrW0WNUu1pn9oyEvTYunb0QdRIgGJkQJHaKOY/R5FCMj9UiD4V8DMPpo10TOXZvUWlPh6PTeCy3H+aT5o37dt51gy8JMP2zHL8u1EeCxPg+TAAAAAElFTkSuQmCC'), auto;
}

.contact_email {
    margin-left: auto;
    margin-top: 13px;
    padding: 3px 7px;
    width: fit-content;
    font-size: 26px;
    font-style: italic;
    font-weight: lighter;
    border-radius: 7px;
    cursor: url('data:./cursor/circuloblanco.png;base64,iVBORw0KGgoAAAANSUhEUgAAAA4AAAAOCAMAAAAolt3jAAAAAXNSR0IB2cksfwAAAAlwSFlzAAALEwAACxMBAJqcGAAAAEVQTFRFAAAA5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfx5Pfxp1coYwAAABd0Uk5TABOJvOyIFE3t/1BhF/f2GYPY1PjwuoZdf0L0AAAAVklEQVR4nF2PWQ6AIAwFH7LviOj9jyqikWW+OknTTAGAbJQxygUaUumGMo9Z/WMB57uGiKQHEvZRM45RC8qseV5eTsXQzbs1AzBfJJNvtOD1hfMidbwBky0GZz0ZqGgAAAAASUVORK5CYII='), pointer; 
}

.email_msn {
    margin-left: auto;
    margin-top: 9px;
    width: fit-content;
    font-size: 13px;
}

@media screen and (min-width: 700px) {
    .contact_container {
        padding-left: 45px;
    }

    .contact_title {
        font-size: clamp(22px, 4vw ,32px);
        width: 30vw;
    }

    .contact_email {
        font-size: clamp(26px, 5.5vw, 48px);
        margin-left: 21vw;
        margin-top: 0px;
    } 

    .email_msn {
        width: 46vw;
        max-width: 414px;
        text-align: right;
        margin-left: 21vw;
    }
}

@media screen and (min-width: 900px) {
    .contact_container {
        padding-left: 75px;
    }

    .contact_email {
        margin-left: 13vw;
    }

    .email_msn {
        margin-left: 13vw;
    }

    .contact_title {
        width: 300px;
    }
}

</style>