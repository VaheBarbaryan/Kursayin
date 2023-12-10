<script setup>
import { ref } from 'vue';

const result = ref(null)
const n = ref(null)

const isHappyNumber = (num) => {
  console.log("NUmber", num);
  if(num == 1 || num == 7) {
    return num
  }
  if(num / 10 < 1) {
    return false
  }
  let sum = 0
  while(num > 0) {
    let t = parseInt(num % 10)
    sum = sum + (t * t)
    num = parseInt(num / 10)
  }
  return isHappyNumber(sum)
}

const nextHappy = (num) => {
  if(!num) {
    return false
  }
  while(true) {
    if(isHappyNumber(++num)) {
      return result.value = num
    }
  }
}

const handleSubmit = () => {
  if(isHappyNumber(n.value)) {
    result.value = `${n.value} is happy number`
  } else {
    result.value = `${n.value} isn't happy number`
  }
}
</script>

<template>
  <h1>Happy Numbers</h1>
  <form class="form">
    <div class="form__row">
      <label for="number" class="form__label"></label>
      <input v-model="n" type="text" id="number" class="form__input">
    </div>
    <button type="button" @click="nextHappy(n)">Submit</button>
  </form>
  <h3>Result` {{ result }}</h3>
</template>

<style scoped>
input {
  width: 100%;
  max-width: 300px;
        margin:15px 0;
        padding:15px 10px;
        width:100%;
        outline:none;
        border:1px solid #bbb;
        border-radius:20px;
        display:inline-block;
        -webkit-box-sizing:border-box;
        -moz-box-sizing:border-box;
        box-sizing:border-box;
        -webkit-transition:0.2s ease all;
        -moz-transition:0.2s ease all;
        -ms-transition:0.2s ease all;
        -o-transition:0.2s ease all;
        transition:0.2s ease all;
        &:focus {
            border-color:cornflowerblue;
        }
    }
</style>