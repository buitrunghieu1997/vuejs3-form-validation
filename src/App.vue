<template>
  <form class="form" @submit.prevent="submit">
    <my-input
        name="Username"
        placeholder="Input your username..."
        type="text"
        :rules="{ required: true, min: 5 }"
        :value="username.value"
        @update="update"
    />
    <my-input
        name="Password"
        placeholder="Input your password..."
        type="password"
        :rules="{ required: true, min: 10 }"
        :value="password.value"
        @update="update"
    />
    <my-button
        color="white"
        background="darkslateblue"
        buttonName="Login"
        :disabled="!valid"
    />
  </form>
</template>

<script>
import MyButton from "@/components/MyButton";
import MyInput from "@/components/MyInput";

export default {
  components: {MyInput, MyButton},
  data() {
    return {
      username: {
        value: '',
        valid: false
      },
      password: {
        value: '',
        valid: false
      },
    }
  },
  methods: {
    update(payload) {
      this[payload.name.toLowerCase()] = {
        value: payload.value,
        valid: payload.valid
      }
    },
    submit($evt) {
      // $evt.preventDefault()
      console.log("Submitted", $evt)
    }
  },
  computed: {
    valid() {
      return this.username.valid && this.password.valid
    }
  }
}
</script>

<style>
body {
  font-family: Arial, serif;
}

.form {
  max-width: 400px;
  width: 50%;
  border: 1px solid lightgray;
  padding: 50px;
  border-radius: 10px;
  margin: auto;
  margin-top: 100px
}
</style>
