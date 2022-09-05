<template>
  <div id="app" style="background-color: #181414 !important;">
    <router-view />
  </div>
</template>
<style></style>
<script>
import { components } from "aws-amplify-vue";
export default {
  name: "app",
  components: {
    ...components
  }
};
</script>