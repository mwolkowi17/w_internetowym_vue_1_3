<script setup>
import { ref,onMounted,onUnmounted } from 'vue'

const emit = defineEmits(['koniec-planszy'])



// przykład obsługi zdarzeń z klawiatury w Vue 3
function handleKeydown(event) {
    if (event.key === 'Enter') {
        console.log('Naciśnięto Enter');
        emit('koniec-planszy');
    }
}

onMounted(() => {document.addEventListener('keydown', handleKeydown);}
)

onUnmounted(() => {
    document.removeEventListener('keydown', handleKeydown);
});
</script>

<template>
    <div class="tlo" aria-label="Plansza startowa"></div>
    <button class="start" @click="$emit('koniec-planszy')" role="img" alt="ikona Start" aria-label="przycisk start"></button>
</template>

<style>
.tytul {
    color: greenyellow;
}

.tlo {
    background-image: url("../assets/plansza_start.png");
    background-size: 1280px 720px;
    height: 720px;
    width: 1280px;
    top: 0px;
    left: 0px;
    position: absolute;
}

.start {
    background-image: url("../assets/START_przycisk.png");
    background-size: 243px 112px;
    background-position: -3px -8px;
    background-repeat: no-repeat;
    position: absolute;
    top: 400px;
    left: 500px;
    width: 240px;
    height: 100px;
    

}

.start:hover {
    cursor: pointer;
}

.start:focus{
    /* border: 4px solid #08e926; */
    outline: thick double #08e926;
}
</style>