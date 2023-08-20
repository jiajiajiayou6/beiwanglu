<template>
  <div class="left11">
    <liebiao></liebiao>
  </div>
</template>

<script>
import liebiao from "../Leftlist/liebiao.vue";
export default {
  name: "BeiwangluLeft",

  data() {
    return {};
  },
  components: {
    liebiao
  },
  mounted() {},

  methods: {}
};
</script>

<style scoped>
.left11 {
  width: 100%;
  height: 100%;
  background: rgb(254, 254, 254);
  border-radius: 8px 0 0 8px;
}
</style>