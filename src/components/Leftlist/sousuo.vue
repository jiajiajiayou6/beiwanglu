<template>
  <div class="sousuo">
    <input type="text" name id="text" placeholder="search" />
  </div>
</template>

<script>
export default {
  name: "BeiwangluSousuo",

  data() {
    return {};
  },

  mounted() {},

  methods: {}
};
</script>

<style scoped>
.sousuo {
  border-radius: 15px 0 0 0;
  width: 100%;
  height: 15%;
  background: salmon;
}
#text {
  width: 80%;
  height: 40px;
  line-height: 40px;
  border-radius: 15px;
  margin-top: 40px;
}
</style>