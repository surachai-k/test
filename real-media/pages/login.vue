<template>
  <div class="login-page">
    <h2>Login</h2>
    <div class="form-container">
      <input type="text" placeholder="username" v-model="username" required />
      <input
        type="password"
        placeholder="password"
        v-model="password"
        required
      />
    </div>
    <button class="btn" type="button" @click="handleLogin">Login</button>
    <br />

    {{ users }}
  </div>
</template>

<script setup>
import axios from "axios";

const config = useRuntimeConfig();

const username = ref("");
const password = ref("");
const users = [
  {
    user: "anan.s@realsmart.co.th",
    password: "anas.s123##",
  },
  {
    user: "surachai.k@realsmart.co.th",
    password: "surachai.k123##",
  },
];
const handleLogin = async () => {
  if (username.value && password.value) {
    const response = (
      await axios.post(`${config.public.realMediaPlayer}/loginToken`, {
        user: username.value,
        password: password.value,
      })
    ).data;

    console.log(response);
  }
};
</script>

<style scoped>
.login-page {
  padding: 12px;
}
.form-container {
  display: flex;
  gap: 12px;
  input {
    padding-left: 8px;
    height: 26px;
  }
}
.btn {
  margin-top: 12px;
}
</style>
