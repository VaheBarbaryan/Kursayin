<script setup>
import { ref, onMounted } from 'vue'

const firstCube = ref(true)
const secondCube = ref(false)
const thirdCube = ref(false)

onMounted(() => {
    setTimeout(() => {
        firstCube.value = false
        secondCube.value = true
    }, 1500)

    setTimeout(() => {
        secondCube.value = false
        thirdCube.value = true
    }, 3000)

    setTimeout(() => {
        thirdCube.value = false
        firstCube.value = true
    }, 4500)

    setTimeout(() => {
        firstCube.value = false
        secondCube.value = true
    }, 6000)

    setTimeout(() => {
        secondCube.value = false
        thirdCube.value = true
    }, 7500)

    setTimeout(() => {
        thirdCube.value = false
    }, 10000)
})


</script>

<template>
  <div class="animation">
    <div v-if="firstCube" class="cube1"></div>
    <div v-if="secondCube" class="cube2"></div>
    <div v-if="thirdCube" class="cube3"></div>
  </div>
</template>

<style lang="scss" scoped>

@keyframes Animation {
    0% {
        right: 10px;
    }

    50% {
        right: 95%;
    }

    75% {
        right: 100%;
    }

    100% {
        right: auto;
        left: 10px;
    }
}


.animation {
    position: relative;
    background: #fff;
    width: 500px;
    height: 350px;
    border-radius: 5px;
    box-shadow: 0 10px 15px rgba(0,0,0, .1);
    padding: 10px;
    .cube1, .cube2, .cube3 {
        position: absolute;
        width: 50px;
        height: 50px;
        background: red;
        animation: Animation 2.5s 0.5s forwards;
    }

    .cube1 {
        top: 10px;
        right: 10px;
    }

    .cube2 {
        top: 20%;
        right: 10px;
    }

    .cube3 {
        bottom: 10px;
        right: 10px;
    }
}
</style>