<template>
  <div class="search">
    <div class="inpt">
      <input type="text" placeholder="search" />
      <span>🔍︎</span>
    </div>
    <div class="list">
      <ul>
        <li
          v-for="item in list"
          :key="item.id"
          @click="stat(item)"
          :class="item.state ? 'bgcol' : ''"
        >
          <div :class="item.state ? 'bord' : ''">
            <img :src="item.img" alt />
            <span>{{ item.title }}</span>
            <a>{{ item.num }}</a>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "BeiwangluSuoyou",

  data() {
    return {
      list: [
        {
          id: 1,
          title: "所有",
          img: "",
          num: 0,
          state: true
        },
        {
          id: 2,
          title: "今天",
          img: "",
          num: 0,
          state: false
        },
        {
          id: 3,
          title: "最近七天",
          img: "",
          num: 0,
          state: false
        }
      ]
    };
  },

  mounted() {},

  methods: {
    stat(item) {
      this.list.forEach(items => {
        items.state = items === item;
      });
    }
  }
};
</script>

<style scoped>
.search {
  padding: 5px;
}
.search .inpt {
  width: 100%;
  height: 50px;
  line-height: 50px;
  text-align: center;
  position: relative;
  border-top-left-radius: 10px;
}
.search .inpt input {
  height: 30px;
  width: 80%;
  border-radius: 10px;
  border: none;
  outline: none;
  background-color: #f3eded;
  padding-left: 10px;
}
.search .inpt span {
  position: absolute;
  right: 25px;
  color: gray;
  font-size: 20px;
}
.search .list {
  height: 150px;
}
.search .list ul {
  border-bottom: 1px solid gray;
}
.search .list li {
  height: 50px;
  font-size: 15px;
  color: gray;
  border-radius: 10px;
  cursor: pointer;
  margin-top: 5px;
}
.search .list li div {
  height: 30px;
  width: 100%;
  line-height: 30px;
  float: left;
  margin-top: 10px;
}
.search .list li:hover {
  background-color: rgba(0, 121, 191, 0.2);
}
.search .list li img {
  width: 15px;
  margin-left: 10px;
}
.search .list li span {
  margin-left: 10px;
}
.search .list li a {
  float: right;
  margin-right: 10px;
}
.bgcol {
  background-color: rgba(0, 121, 191, 0.2);
}
.bord {
  border-left: 3px solid rgb(6, 138, 240);
}
</style>