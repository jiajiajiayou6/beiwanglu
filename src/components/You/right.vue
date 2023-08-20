<template>
  <div class="right1">
    <h2 class="qqq1">所有</h2>
    <ul>
      <li class="suoyouliebiao">
        <div class="suoyoushang">
          <input class="suoyouleft" type="checkbox" />
          <input class="suoyouleft1" type="text" v-model="content" />
          <span class="suoyouright">删除</span>
          <span class="suoyouright">...</span>
        </div>
        <div class="suoyouxia"></div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "BeiwangluRight",

  data() {
    return {
      content: "aaaa",
      contValue: ""
    };
  },

  mounted() {},

  methods: {}
};
</script>

<style scoped>
.right1 {
  width: 100%;
  height: 100%;
  /* background: rgb(209, 80, 80); */
}
.qqq1 {
  height: 50px;
  display: block;
  margin-left: -80%;
}
.suoyouliebiao {
  width: 86%;
  height: 60px;
  background: white;
  margin: auto;
  border-radius: 8px;
}
.suoyoushang {
  width: 100%;
  height: 30px;
  background: aqua;
  border-radius: 8px 8px 0 0;
  line-height: 30px;
}
.suoyouleft {
  width: 16px;
  height: 16px;
  margin: 7px;
  float: left;
}
.suoyouleft1 {
  margin: 5px;
  border: none;
  float: left;
}
.suoyouxia {
  width: 100%;
  height: 30px;
  background: hotpink;
  border-radius: 0 0 8px 8px;
  line-height: 30px;
}
.suoyouright {
  float: right;
}
</style>