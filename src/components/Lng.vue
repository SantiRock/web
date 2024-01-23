<script setup>
import { contentapi } from './content';
const emit =defineEmits(['lng'])

function eslng () {
    emit('lng', contentapi.es)
}

function enlng () {
    emit('lng', contentapi.en)
}

</script>

<template>
    <div class="lng_container">
        <div class="languages">
            <button class="lng_btn" @click="eslng">Es</button>
            <button class="lng_btn" @click="enlng">En</button>
        </div>
    </div>
</template>

<style>

.languages {
    position: fixed;
    top: 53px;
    right: 19px;
    width: fit-content;

}

.lng_btn {
    display: block;
    margin-bottom: 7px;
    font-size: 18px;
    font-style: italic;
    font-weight: bold;
    color: var(--verde-claro);
    cursor: url('data:./cursor/circulopeke.png;base64,iVBORw0KGgoAAAANSUhEUgAAAAUAAAAFBAMAAAB/QTvWAAAAAXNSR0IB2cksfwAAAAlwSFlzAAALEwAACxMBAJqcGAAAAA9QTFRFsuLSsuLSsuLSsuLSsuLSLoMBBAAAAAV0Uk5TG7TwvP+X/QQGAAAAF0lEQVR4nGNgVGRgMHExYFBxUQDTQD4AFToCHQBzmSoAAAAASUVORK5CYII=') 0 0, pointer;
}

.lng_btn:hover {
    color: white;
    font-weight: normal;
}

@media screen and (min-width: 641px) {
    .lng_container {
        position: relative;
        max-width: 1280px;
        margin: auto;
    }

    .languages {
        position: absolute;
        top: 13px;
        left: 13px;
    }

    .lng_btn {
        display: inline;
        margin-left: 13px;
        color: white;
    }

    .lng_btn:hover {
        color: var(--verde-claro);
    }
    
}

</style>