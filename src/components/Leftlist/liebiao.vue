<template>
  <div class="zuolie">
    <!-- <sousuo></sousuo> -->
    <suoyou></suoyou>
  </div>
</template>

<script>
// import sousuo from "./sousuo.vue";s
import suoyou from "./suoyou.vue";
export default {
  name: "BeiwangluLiebiao",

  data() {
    return {};
  },
  components: {
    // sousuo,
    suoyou
  },
  mounted() {},

  methods: {}
};
</script>

<style scoped>
.zuolie {
  width: 100%;
  height: 100%;
  /* background: rosybrown; */
}
</style>