<template>
  <div
    class="container"
    :alertType="alertType"
    :style="[
      alertType === 'info'
        ? { backgroundColor: '#f4faff', borderColor: primaryColor }
        : alertType === 'error'
        ? { backgroundColor: '#FEF5F5', borderColor: errorColor }
        : alertType === 'warning'
        ? { backgroundColor: '#FDF3E1', borderColor: warningColor }
        : { backgroundColor: '#F8FFF2', borderColor: successColor },
    ]"
  >
    <font-awesome-icon
      :icon="
        alertType === 'info'
          ? 'fa-solid fa-circle-info'
          : alertType === 'error'
          ? 'fa-solid fa-circle-exclamation'
          : alertType === 'warning'
          ? 'fa-solid fa-triangle-exclamation'
          : 'fa-solid fa-circle-check'
      "
      :style="[
        alertType === 'info'
          ? { color: '#2c75dd' }
          : alertType === 'error'
          ? { color: '#CC3123' }
          : alertType === 'warning'
          ? { color: '#C75100' }
          : { color: '#008700' },
      ]"
      size="xl"
    />
    <div class="text-container">
      <p v-if="title" class="title">A short descriptive header</p>
      <p v-if="description" class="description">
        This is a paragraph of information with additional supporting detail or
        links to help the user understand what they should do.
      </p>

      <div v-if="title && description" class="btn-container">
        <AppButton
          class="secondary-btn"
          button-type="secondary"
          :color="
            alertType === 'info'
              ? infoColor
              : alertType === 'error'
              ? errorColor
              : alertType === 'warning'
              ? warningColor
              : successColor
          "
        ></AppButton>
        <AppButton
          :color="
            alertType === 'info'
              ? infoColor
              : alertType === 'error'
              ? errorColor
              : alertType === 'warning'
              ? warningColor
              : successColor
          "
        ></AppButton>
      </div>
    </div>
    <button class="close-btn" @click="closeBtn">
      <font-awesome-icon icon="fa-solid fa-xmark" size="lg" />
    </button>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import AppButton from './AppButton.vue'

const infoColor = ref('#F7BA50')
const primaryColor = ref('#2c75dd')
const errorColor = ref('#CC3123')
const warningColor = ref('#C75100')
const successColor = ref('#008700')

const emit = defineEmits(['closeAlert'])

const props = defineProps({
  alertType: {
    type: String,
    default: 'info',
  },
  title: {
    type: Boolean,
    default: true,
  },
  description: {
    type: Boolean,
    default: true,
  },
})

const closeBtn = () => {
  emit('closeAlert', false)
}
</script>

<style scoped>
p {
  color: #0c0d0d;
  text-align: left;
  margin-top: 0;
}
p.title {
  font-weight: 600;
}
div.container {
  display: flex;
  padding: 26px;
  border: 1px solid;
}
div.text-container {
  margin-left: 14px;
  width: 720px;
}
div.btn-container {
  display: flex;
}
.secondary-btn {
  margin-right: 16px;
}
button.close-btn {
  all: unset;
  background-color: transparent;
  height: 0;
  cursor: pointer;
}
button.close-btn:hover {
  border: none;
}

@media only screen and (max-width: 600px) {
  div.text-container {
    width: 234px;
  }
  div.btn-container {
    flex-direction: column;
  }
  .secondary-btn {
    margin-bottom: 16px;
  }
}
</style>
