<script setup>
import { ref } from 'vue'

import HomeView from './HomeView.vue'
import AboutView from './AboutView.vue'
import HelpView from './HelpView.vue'

import Swal from 'sweetalert2'

const emit = defineEmits(['logout'])

const currentPage = ref('home')
const menuVertical = ref(false)

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

const openHelpModal = () => {
  Swal.fire({
    title: 'Info Modal',
    text: 'Help topic.',
    icon: 'question',
  });
}

const openTipModal = () => {
  Swal.fire({
    title: 'Tip of the Day',
    text: `
      How to set entire document editable
      
      document.designMode = 'on';
    `,
    icon: 'info',
  });
}

const handleLogout = () => {
  console.log('Logging out...');
  emit('logout')
};
</script>

<template>
  <div class="main">
    <h1 class="main__title">Advert Application</h1>
    <div class="main__header" :class="{[`main__header-vertical`]: menuVertical}">
      <button @click="menuVertical = !menuVertical"><font-awesome-icon :icon="['fas', 'ellipsis-vertical']" /></button>
      <button @click="openHelpModal"><font-awesome-icon :icon="['fas', 'circle-info']" /></button>
      <button @click="openTipModal">Tip of the Day</button>
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
    width: calc(100% - 50px);

    &__title {
      margin-top: 0;
      text-align-last: left;
    }

    &__header {
      display: flex;
      align-items: flex-start;
      gap: 10px;
      margin-bottom: 20px;

      &-vertical {
        flex-direction: column;
      }
    }
}
</style>