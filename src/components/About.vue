<script setup>

</script>

<template>
    <section class="about_container" id="about">
      <div class="about_c1">
        <h2 class="about_title">¿Que onda?</h2>
        <p class="about_name">Santiago Quintero</p>
      </div>
      <p class="about_bio">Egresado de la escuela de cine, me interesé por las artes audiovisuales expandidas lo que me condujo a la programación, en la cual encontré una verdadera pasión.</p>
    </section>
</template>

<style>

.about_container {
    margin: auto; 
    margin-bottom: 27px;
    padding: 21px 35px;
    max-width: 1280px;
    min-width: 320px;
}

.about_title {
    width: fit-content;
    font-size: 24px;
    font-style: italic;
    font-weight: lighter;
}

.about_name {
    margin-top: 7px;
    margin-bottom: 19px;
    width: fit-content;
    font-size: 16px;
    font-style: italic;
    font-weight: lighter;
}

.about_bio {
    max-width: 400px;
    font-size: 15px;
    line-height: 2;
}

@media screen and (min-width: 700px) {
    .about_container {
        display: flex;
        justify-content: center;
        padding-left: 45px;
        gap: 5%;
    }

    .about_title {
        font-size: 32px;
    }
    
    .about_name {
        font-size: 20px;
    }
}

@media screen and (min-width: 900px) {
    .about_container {
        margin-top: 33px;
    }

    .about_title {
        font-size: 64px;
    }

    .about_name {
        padding-left: 150px;
        font-size: 32px;
    }
    
    .about_bio {
        margin-top: 13px;
    }
}

</style>
