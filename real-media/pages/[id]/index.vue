<template>
  <div>
    <h3>Video</h3>
    Content id:{{ contentId }}
    <br />
    <video
      width="620"
      height="440"
      controls
      :src="`http://54.169.131.49:8081/api/player/${contentId}`"
    ></video>
  </div>
</template>

<script setup>
import { useRoute } from "vue-router";

const route = useRoute();
const contentId = route.params.id;
</script>

<style lang="scss" scoped></style>
