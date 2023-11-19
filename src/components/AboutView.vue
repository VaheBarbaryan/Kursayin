<script setup>
import adImg from '../assets/ad.jpg'
</script>

<template>
  <div class="about">
    <h1 class="about__title">Author is Vahe Barbaryan Karen, Yerevan State College of Informatics</h1>
    <img class="about__img" :src="adImg" alt="advertisement">
  </div>
</template>

<style lang="scss" scoped>
.about {
  max-width: 100%;
}
</style>