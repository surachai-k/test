<template>
  <div>
    <h3>Video</h3>
    Content id:{{ contentId }}
    <br />
    <video
      width="620"
      height="440"
      controls
      :src="config.public.realMediaPlayer + '/' + contentId"
    ></video>
  </div>
</template>

<script setup>
import { useRoute } from "vue-router";

const config = useRuntimeConfig();
const route = useRoute();
const contentId = route.params.id;
</script>

<style lang="scss" scoped></style>
