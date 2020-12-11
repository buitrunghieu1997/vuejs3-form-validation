<template>
  <div class="button-wrapper">
    <button
        :style="{ background, color }"
        :disabled="disabled"
    >
      {{ buttonName }}
    </button>
  </div>
</template>

<script>
export default {
  props: {
    color: {
      type: String
    },
    background: {
      type: String
    },
    disabled: {
      type: Boolean
    },
    buttonName: {
      type: String,
      default: 'Button'
    },
  }
};
</script>

<style scoped>
button {
  background: none;
  color: black;
  border: none;
  border-radius: 5px;
  padding: 10px 40px;
  font-size: 16px;
  cursor: pointer;
  margin: 10px auto;
}

button:hover {
  filter: brightness(125%)
}

button:disabled {
  opacity: 0.5;
}

.button-wrapper {
  margin-top: 20px;
  text-align: center;
}
</style>
