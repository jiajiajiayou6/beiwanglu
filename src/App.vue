<template>
  <div id="app">
    <tubiao></tubiao>
  </div>
</template>

<script>
import tubiao from "./components/Zhuti/Neirong.vue";

export default {
  name: "App",
  components: {
    tubiao
  }
};
</script>
<style>
* {
  margin: 0;
  padding: 0;
}
li {
  list-style: none;
}
a {
  text-decoration: none;
}
</style>
<style scoped>
#app {
  width: 100%;
  height: 100vh;
  background-image: url("https://ms.bdimg.com/pacific/0/pic/451651596_1052400716.jpg?x=0&y=0&h=340&w=510&vh=340.00&vw=510.00&oh=340.00&ow=510.00");
  background-size: 100% 100%;
}
</style>


