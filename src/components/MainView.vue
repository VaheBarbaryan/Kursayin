<script setup>
import { ref } from 'vue'

import HomeView from './HomeView.vue'
import AboutView from './AboutView.vue'
import HelpView from './HelpView.vue'

import Swal from 'sweetalert2'

const emit = defineEmits(['logout'])

const currentPage = ref('home')

const openLogoutModal = () => {
  Swal.fire({
    title: 'Are you sure you want to logout?',
    text: 'You will be logged out of your account.',
    icon: 'warning',
    showCancelButton: true,
    confirmButtonColor: '#3085d6',
    cancelButtonColor: '#d33',
    confirmButtonText: 'OK',
    cancelButtonText: 'Cancel'
  }).then((result) => {
    if (result.isConfirmed) {
      handleLogout();
    }
  });
}

const handleLogout = () => {
  console.log('Logging out...');
  emit('logout')
};
</script>

<template>
  <div class="main">
    <div class="main__header">
      <button @click="currentPage = 'home'">Home</button>
      <button @click="currentPage = 'about'">About</button>
      <button @click="currentPage = 'help'">Help</button>
      <button @click="openLogoutModal">Logout</button>
    </div>
    <home-view v-if="currentPage === 'home'" />
    <about-view v-if="currentPage === 'about'" />
    <help-view v-if="currentPage === 'help'" />
  </div>
</template>

<style lang="scss" scoped>
.main {
    background: #fff;
    padding: 30px;

    &__header {
      display: flex;
      align-items: center;
      gap: 10px;
      margin-bottom: 20px;
    }
}
</style>