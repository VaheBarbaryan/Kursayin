<script setup>
import { onMounted, reactive } from 'vue'

import Animation from '@/components/Animation.vue'
import Login from '@/components/Login.vue'
import NewPassword from '@/components/NewPassword.vue'
import MainView from '@/components/MainView.vue'

const authUser = {
    email: 'test@gmail.com',
    password: '123456789'
}

const state = reactive({
  animation: true,
  login: false,
  newPassword: false,
  main: false
})

const onSubmit = (value) => {
  state.login = false
  if(!value) {
    state.newPassword = true
  } else {
    state.main = true
  }
}

const setNewPassword = (password) => {
  console.log("New Password", password.value);
  authUser.password = password.value
  state.newPassword = false
  state.main = true
}

const handleLogout = () => {
  state.main = false
  state.login = true
}

onMounted(() => {
  setTimeout(() => {
    state.animation = false
    state.login = true
  },10000)
})
</script>

<template>
  <div>
    <Animation v-if="state.animation" />
    <Login v-if="state.login" :authUser="authUser" @submit="onSubmit" />
    <NewPassword v-if="state.newPassword" :authUser="authUser" @submit="setNewPassword" />
    <MainView v-if="state.main" :authUser="authUser" @logout="handleLogout" />
  </div>
</template>

<style scoped>

</style>
