<template>
  <div>
    <button
      :buttonType="buttonType"
      :class="[
        buttonType === 'primary' ? 'primary' : 'secondary',
        { 'icon-only': iconOnly },
      ]"
    >
      <!-- prepend icon -->
      <font-awesome-icon
        v-if="prependIcon"
        :class="{ prepend: prependIcon }"
        icon="fa-solid fa-arrow-right"
        size="lg"
      />

      <!-- icon only or text only btn -->
      <span v-if="iconOnly">
        <font-awesome-icon icon="fa-solid fa-arrow-right" size="lg" />
      </span>
      <span v-else>Active</span>

      <!-- append icon -->
      <font-awesome-icon
        v-if="appendIcon"
        :class="{ append: appendIcon }"
        icon="fa-solid fa-arrow-right"
        size="lg"
      />
    </button>
  </div>
</template>

<script setup>
defineProps({
  buttonType: {
    type: String,
    default: 'primary',
  },
  prependIcon: {
    type: Boolean,
    default: false,
  },
  appendIcon: {
    type: Boolean,
    default: false,
  },
  iconOnly: {
    type: Boolean,
    default: false,
  },
})
</script>

<style scoped>
button {
  border-radius: 8px;
  padding: 6px 12px;
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
.prepend {
  margin-right: 4px;
}
.append {
  margin-left: 4px;
}
.icon-only {
  width: 40px;
  height: 40px;
}
</style>
