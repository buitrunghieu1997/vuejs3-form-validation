<template>
  <div class="input-wrapper">
    <div class="label">
      <label :for="name">{{ name }}</label>
      <div class="error">{{ error }}</div>
    </div>
    <input
        :id="name"
        :type="type"
        :value="value"
        :placeholder="placeholder"
        @input="input"
    />
  </div>
</template>

<script>
export default {
  props: {
    name: {
      type: String,
      required: true
    },
    type: {
      type: String,
      required: true
    },
    rules: {
      type: Object, // min, require
    },
    value: {
      type: String,
    },
    placeholder: {
      type: String,
      default: ''
    },
  },
  computed: {
    error () {
      return this.validate(this.value)
    }
  },
  methods: {
    validate(value) {
      if (this.rules.required && !value) {
        return "Required"
      }
      if (this.rules.required && value.length < this.rules.min) {
        return `Minimum length is ${this.rules.min} characters`
      }
      return ""
    },
    input ($evt) {
      this.$emit('update', {
        value: $evt.target.value,
        name: this.name,
        valid: !this.validate($evt.target.value)
      })
    }
  }
}
</script>

<style scoped>
.input-wrapper {
  display: flex;
  flex-direction: column;
}

.label {
  display: flex;
  justify-content: space-between;
  padding-top: 10px;
}

.error {
  color: red;
  font-size: 10px;
  font-style: italic;
}

input {
  background: none;
  color: black;
  border: 1px solid silver;
  border-radius: 5px;
  padding: 10px;
  font-size: 16px;
  margin: 5px 0
}
</style>
