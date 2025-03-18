<template>
  <div class="login-page">
    <h2>Login</h2>
    <div class="form-container">
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

const route = useRoute();
const config = useRuntimeConfig();
const cookie = useCookie("token");
const domain = useCookie("rsmedia");

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
  if (password.value) {
    const redirect = route.query.redirect;
    const response = (
      await axios.post(`${config.public.realMediaPlayer}/loginToken`, {
        password: password.value,
      })
    ).data;

    if (response.token) {
      cookie.value = response.token;

      // window.location.href = `${config.public.realMediaPlayer}${redirect}`;
      await navigateTo(`${config.public.realMediaPlayer}${redirect}`, {
        external: true,
      });
    }
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
