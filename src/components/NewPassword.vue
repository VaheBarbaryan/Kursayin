<script setup>
import { ref } from "vue"

const props = defineProps(['authUser'])

const emit = defineEmits(['submit'])

const newPassword = ref('')
const ConfirmNewPassword = ref('')

const onSubmit = () => {
   if(ConfirmNewPassword.value === '' || newPassword.value === '' || ConfirmNewPassword.value !== newPassword.value) {
        return false
   } else {
    emit('submit', newPassword)
   }
}

</script>

<template>
  <form class="new-password">
    <label for="new_password">New Password</label>
    <input v-model="newPassword" type="password" id="new_password" placeholder="Enter New Password">
    <label for="confirm_new_password">Confirm New Password</label>
    <input v-model="ConfirmNewPassword" type="password" id="confirm_new_password" placeholder="Confirm New Password">
    <button @click="onSubmit" type="button" class="submit">Submit</button>
  </form>
</template>

<style lang="scss" scoped>
.new-password {
    box-shadow: 0 10px 15px rgba(0,0,0, .1);
    padding:30px;
	width:400px;
	height:auto;
	overflow:hidden;
	background:white;
	border-radius:10px;
    label {
        font-size:14px;
        color:darkgray;
        cursor:pointer;
    }

    label,
    input {
        float:left;
        clear:both;
    }

    input {
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
}
</style>