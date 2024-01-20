<script setup>
</script>

<template>
    <footer class="footer_container">
        <p class="footer_p">Desarrollado por <span class="footer_name">Santiago Quinter</span> en <span class="footer_name">Vue.js</span> - © 2024</p>
    </footer>

</template>

<style>
.footer_container {
    margin: auto;
    min-width: 320px;
    text-align: center;
    padding-bottom: 27px;
}

.footer_p {
    font-size: 13px;
    font-style: italic;
    font-weight: lighter;
}

.footer_name {
    color: var(--verde-claro)
}

@media screen and (min-width: 450px) {
    .footer_p {
        font-size: 15px;
    }  
}

</style>