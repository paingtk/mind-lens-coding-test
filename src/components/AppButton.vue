<template>
  <button
    :buttonType="buttonType"
    class="btn"
    :class="[
      buttonType === 'primary' ? 'primary' : 'secondary',
      { 'icon-only': iconOnly },
    ]"
    :style="[
      buttonType === 'primary'
        ? { backgroundColor: color }
        : { borderColor: color, color: color },
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
    <span class="btn-text" v-else>Action</span>

    <!-- append icon -->
    <font-awesome-icon
      v-if="appendIcon"
      :class="{ append: appendIcon }"
      icon="fa-solid fa-arrow-right"
      size="lg"
    />
  </button>
</template>

<script setup>
defineProps({
  color: {
    type: String,
    default: '#f7ba50',
  },
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
}
button:focus {
  outline: none;
}
button.secondary {
  background-color: none;
}
button:hover {
  filter: drop-shadow(0px 6px 10px rgba(0, 0, 0, 0.14))
    drop-shadow(0px 1px 18px rgba(0, 0, 0, 0.12));
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
button.primary span.btn-text {
  color: #eee;
}
</style>
