<template>
  <div>
    <h3>Audio</h3>
    Content id:{{ contentId }}
    <br />
    <audio
      controls
      :src="config.public.realMediaPlayer + '/' + contentId"
    ></audio>
  </div>
</template>

<script setup>
import { useRoute } from "vue-router";

const config = useRuntimeConfig();
const route = useRoute();
const contentId = route.params.id;
</script>

<style lang="scss" scoped></style>
