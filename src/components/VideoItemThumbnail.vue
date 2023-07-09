<template>
  <div class="relative">
    <img :src="`https://picsum.photos/seed/image${index}/720/404`" />
    <video-item-thumbnail-btn label="watch later" icon="clock" class="top-0"></video-item-thumbnail-btn>
    <video-item-thumbnail-btn label="Add to queue" icon="menuAlt3" class="top-8"></video-item-thumbnail-btn>
  </div>
</template>

<script>
import BaseIcon from "./BaseIcon.vue";
import VideoItemThumbnailBtn from './VideoItemThumbnailBtn.vue';
export default {
  components: { BaseIcon, VideoItemThumbnailBtn },
  props: ["index"],
};
</script>

<style></style>
