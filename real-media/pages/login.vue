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
      //   const result = await axios.get(
      //     `https://rsmedia.realsmart.co.th${redirect}`,
      //     {
      //       headers: {
      //         Authorization: `${response.token}`,
      //       },
      //     }
      //   );

      //   // Axios won't handle redirects automatically, so manually navigate
      //   if (result.status === 200) {
      window.open(
        `https://rsmedia.realsmart.co.th${redirect}?token=${response.token}`,
        "_blank"
      );
      //   window.location.replace(
      //     `https://rsmedia.realsmart.co.th${redirect}?token=${response.token}`
      //   );
      //   window.location.href = `https://rsmedia.realsmart.co.th${redirect}?token=${response.token}`;
      // `https://rsmedia.realsmart.co.th${redirect}`;
      //   }
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
