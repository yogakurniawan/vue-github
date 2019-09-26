<template>
  <content-loader
    :height="90"
    :width="400"
    :speed="4"
    primaryColor="#f3f3f3"
    secondaryColor="#cac8c8"
  >
    <rect x="9.69" y="0" rx="3" ry="3" width="376.98" height="25" />
    <rect x="9.69" y="30" rx="3" ry="3" width="376.98" height="25" />
    <rect x="9.69" y="60" rx="3" ry="3" width="376.98" height="25" />
  </content-loader>
</template>
    
<script>
import { ContentLoader } from "vue-content-loader";

export default {
  components: {
    ContentLoader
  }
};
</script>
