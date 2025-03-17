<template>
  <div>
    <h3>Audio</h3>
    Content id:{{ contentId }}
    <br />
    <button @click="handleDownload" type="button">Download media</button>
    <br />
    <audio
      ref="audio"
      width="620"
      height="440"
      controls
      controlslist="nodownload"
    >
      <source :src="config.public.realMediaPlayer + '/auth/player/' + contentId" />
    </audio>
  </div>
</template>

<script setup>
import { useRoute } from "vue-router";

const config = useRuntimeConfig();
const route = useRoute();
const contentId = route.params.id;
const audio = ref(null);

const handleDownload = () => {
  const downloadUrl = `${config.public.realMediaPlayer}/auth/download/${contentId}`;
  const link = document.createElement("a");
  link.href = downloadUrl;
  link.download = "custom-video.mp4";
  document.body.appendChild(link);
  link.click();
  document.body.removeChild(link);
};
</script>

<style lang="scss" scoped></style>
