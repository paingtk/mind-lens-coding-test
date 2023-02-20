<script setup>
import { ref } from 'vue'
import AppAlertBox from './components/AppAlertBox.vue'
import AppButton from './components/AppButton.vue'

const showAlertBox = ref(false)

const onClick = () => {
  showAlertBox.value = !showAlertBox.value
}
</script>

<template>
  <h3>Mind Lens Coding Test</h3>
  <AppButton v-if="!showAlertBox" @click="onClick" />
  <AppAlertBox
    v-if="showAlertBox"
    alert-type="warning"
    @closeAlert="onClick"
  ></AppAlertBox>
</template>

<style scoped>
input {
  width: 40%;
  height: 30px;
  border-radius: 0.5rem;
  margin-right: 10px;
}
</style>
