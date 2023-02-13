<template>
  <div>
    <button
      :buttonType="buttonType"
      :class="[buttonType === 'primary' ? 'primary' : 'secondary']"
    >
      Action
    </button>
  </div>
</template>

<script setup>
defineProps({
  buttonType: {
    type: String,
    default: 'secondary',
  },
})
</script>

<style scoped>
button {
  border-radius: 8px;
  padding: 6px 12px;
  font-size: 16px;
  font-weight: 600;
  font-family: inherit;
  width: 130px;
  height: 40px;
  cursor: pointer;
  transition: border-color 0.25s;
}
button.primary {
  background-color: #f7ba50;
}
button.secondary {
  border-color: #c75100;
  color: #c75100;
  background-color: none;
}
button:hover {
  filter: drop-shadow(0px 6px 10px rgba(0, 0, 0, 0.14))
    drop-shadow(0px 1px 18px rgba(0, 0, 0, 0.12));
}
button.primary:hover {
  background-color: #f5ab2b;
}
/* button:focus,
button:focus-visible {
  outline: 4px auto -webkit-focus-ring-color;
} */
</style>
