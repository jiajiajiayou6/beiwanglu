<template>
  <div class="danban">
    <div v-show="this.index==1" class="wwww" @click="bianda">
      <img
        class="eeee"
        alt="Vue logo"
        src="https://img2.baidu.com/it/u=1863744683,2997048396&fm=253&fmt=auto&app=138&f=PNG?w=500&h=500"
      />
      <HelloWorld msg="待办事项" />
    </div>
    <div v-show="this.index==2" class="aaaa">
      <div class="left">
        <div class="search">
          <div class="inpt">
            <input type="text" placeholder="search" v-model="searchValue" @input="search()" />
            <span>🔍︎</span>
          </div>
          <div class="list">
            <ul>
              <li
                v-for="(item,index)  in list"
                :key="item.id"
                @click="stat(item.id,index)"
                :class="ids==item.id?'bgcol':''"
              >
                <div :class="ids==item.id ? 'bord' : ''">
                  <img :src="item.img" alt />
                  <span style="float: left;margin-left:30px">{{ item.title }}</span>
                  <a>{{ item.con.length }}</a>
                </div>
              </li>
            </ul>
            <!-- <ul class="ulll">
              <li v-for="(item)  in list1" :key="item.title">{{ item.title }}</li>
            </ul>-->
            <div class="xinjian" @click="tianjia">
              <span style="float: left;margin-left:30px">🪮新建列表</span>
            </div>
          </div>
        </div>
      </div>
      <!-- :class="item.state ? 'bgcol' : ''" -->
      <div class="right">
        <div class="right1">
          <span class="aes1" @click="bianxiao">X</span>
          <span class="suoyouright1">...</span>
          <h2 class="qqq1">{{kong.title}}</h2>
          <div v-if="kong.con.length==0">快来添加待办事项吧</div>
          <ul class="zongliebiao" v-if="kong.con.length!==0">
            <li class="suoyouliebiao" v-for="(item,index) in kong.con" :key="item.name">
              <div class="suoyoushang">
                <input class="suoyouleft" v-model="item.content" type="checkbox" />
                <input
                  class="suoyouleft1"
                  type="text"
                  v-model="item.ba"
                  :style="item.content==true?'text-decoration: line-through;':'text-decoration: none;'"
                />
                <span class="suoyouright" @click="shanchu(index)">一</span>
                <span class="suoyouright1">...</span>
              </div>
              <div class="suoyouxia">
                <el-date-picker
                  style="float:left;margin-left:20px;border:none !important;"
                  v-model="item.time"
                  type="date"
                  format="yyyy 年 MM 月 dd 日"
                  value-format="yyyy-MM-dd"
                ></el-date-picker>
              </div>
            </li>
          </ul>
          <div class="suoyouzhixia">
            <input
              class="wianjiaduixaing"
              type="text"
              v-model="contt"
              style="border:2px solid #efefef;margin-left:10px"
              placeholder="🪮添加新任务"
              @keyup.enter="huiche"
              id
            />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import HelloWorld from "../HelloWorld.vue";
// import right from "../You/right.vue";
// import right_s from "../You/right_s.vue";
// import youList from "../You/youList.vue";
export default {
  name: "BeiwangluNeirong",

  data() {
    return {
      searchValue: "",
      value2: "",
      index: 1,
      list: [
        {
          id: 1,
          title: "所有",
          img: "",
          num: 0,
          state: true,
          con: [
            {
              ba: "sas",
              content: false,
              time: ""
            },
            {
              ba: "sas",
              content: false,
              time: ""
            },
            {
              ba: "sas",
              content: false,
              time: ""
            },
            {
              ba: "sas",
              content: false,
              time: ""
            },
            {
              ba: "sas",
              content: false,
              time: ""
            },
            {
              ba: "sas",
              content: false,
              time: ""
            },
            {
              ba: "sas",
              content: false,
              time: ""
            }
          ]
        },
        {
          id: 2,
          title: "今天",
          img: "",
          num: 0,
          state: false,
          con: [
            {
              ba: "sa1234s",
              content: false
            },
            {
              ba: "sas12345",
              content: false
            },
            {
              ba: "sas1234",
              content: false
            },
            {
              ba: "sas12345t",
              content: false
            }
          ]
        },
        {
          id: 3,
          title: "最近七天",
          img: "",
          num: 0,
          state: false,
          con: []
        }
      ],
      list1: [],
      ids: 1,
      current: "right",
      kong: {},
      contt: ""
    };
  },
  components: {
    HelloWorld
    // right,
    // right_s,
    // youList
  },
  mounted() {
    this.kong = this.list[0];
  },

  methods: {
    // 搜索
    search() {
      this.list.forEach((item, index) => {
        if (item.id == this.ids) {
          this.list1 = this.list[index].con.filter(item => {
            return item.ba.includes(this.searchValue);
          });
        }
      });
    },
    bianda() {
      this.index = 2;
      //   console.log(4556);
    },
    bianxiao() {
      this.index = 1;
      //   console.log(4556);
    },
    stat(id, index) {
      this.ids = id;
      this.kong = this.list[index];
      // this.list.forEach(items => {
      //   items.state = items === item;
      // });
      // if (id == 1) {
      //   this.kong = this.list[index].con;
      // } else if (id == 2) {
      //   this.current = "right_s";
      // } else if (id == 3) {
      //   this.current = "youList";
      // }
    },
    tianjia() {
      let qwertq = {
        id: this.list.length + 1,
        title: "待办事项",
        img: "",
        num: 0,
        state: false,
        con: []
      };
      this.list.push(qwertq);
    },
    huiche() {
      let obj = {
        ba: this.contt,
        content: false
      };

      this.list.forEach((item, index) => {
        if (this.contt === " ") {
          return alert("不能为空");
        } else if (item.id == this.ids) {
          if (index == 0) {
            this.list[0].con.unshift(obj);
          } else {
            this.list[index].con.unshift(obj);
            this.list[0].con.unshift(obj);
          }
        }
      });
      this.contt = "";
    },
    shanchu(indexs) {
      this.list.forEach((item, index) => {
        if (item.id == this.ids) {
          this.list[index].con.splice(indexs, 1);
        }
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
.wergt {
  width: 90%;
  height: 30px;
  line-height: 30px;
  border: none;
}
.search .inpt input {
  height: 30px;
  width: 80%;
  border-radius: 10px;
  border: none;
  outline: none;
  background-color: #e8e8e8;
  padding-left: 10px;
}
.search .inpt span {
  position: absolute;
  right: 25px;
  color: gray;
  font-size: 20px;
}
.aes1 {
  width: 30px;
  height: 30px;
  line-height: 30px;
  float: right;
  border-radius: 20px;
  background: rgb(223, 223, 223);
}
.aes1:hover {
  background: red;
  color: white;
}
.search .list {
  height: 150px;
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
.danban {
  width: 100%;
  height: 100%;
}
.xinjian {
  width: 25%;
  height: 40px;
  line-height: 40px;
  background: rgb(255, 255, 255);
  position: absolute;
  border-radius: 8px;
  bottom: 0;
}
.wwww {
  width: 250px;
  height: 250px;
  position: relative;
  top: 40%;
}
.eeee {
  width: 200px;
  height: 200px;
}
.aaaa {
  width: 1100px;
  height: 600px;
  position: absolute;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  margin: auto;
  /* background: rgb(127, 186, 228); */
  border-radius: 15px;
  display: flex;
}
.left {
  width: 25%;
  height: 100%;
  border-radius: 15px 0 0 15px;
  background: #fff;
}
.right {
  width: 75%;
  height: 100%;
  background-color: #e8e8e8;
  border-radius: 0 8px 8px 0;
}
.right1 {
  width: 100%;
  height: 100%;
  /* background: rgb(209, 80, 80); */
}
.qqq1 {
  height: 50px;
  display: block;
  margin-left: -70%;
  margin-top: 10px;
}
.ulll {
  width: 100%;
  height: 400px;
  overflow: auto;
}

.ulll li {
  width: 100%;
  height: 60px;
  line-height: 60px;
}
.suoyouliebiao {
  width: 86%;
  height: 70px;

  background: white;
  margin: auto;
  border-radius: 8px;
  margin-top: 10px;
}
.suoyouzhixia {
  width: 75%;
  border-radius: 0 0 8px 0;
  height: 70px;
  line-height: 70px;
  position: absolute;
  bottom: 0;
  z-index: 2;
  background: rgb(255, 255, 255);
}
.wianjiaduixaing {
  width: 80%;
  height: 40px;
  margin-left: 20px;
}
.zongliebiao {
  width: 100%;
  height: 80%;
  overflow: auto;
}
::-webkit-scrollbar {
  /*隐藏滚轮*/
  display: none;
}
.suoyoushang {
  width: 100%;
  height: 30px;
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
  margin: 2.5px;
  height: 25px;
  border: none;
  float: left;
  outline: none;
}
.suoyouxia {
  width: 100%;
  height: 40px;
  border-radius: 0 0 8px 8px;
  line-height: 40px;
}
.suoyouright {
  float: right;
  width: 40px;
  margin-left: 10px;
  text-align: center;
  border-radius: 8px;
  background: rgb(239, 239, 239);
}
.suoyouright1 {
  float: right;
  width: 50px;
  height: 30px;
  margin-right: 10px;
  border-radius: 8px;
  background: rgb(232, 232, 232);
}
.wianjiaduixaing {
  width: 80%;
  height: 40px;
}
</style>