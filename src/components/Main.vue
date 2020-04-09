<template>
  <div class="home">
    <el-row :gutter="10">
      <el-col :span="8">
        <h1>全部书籍</h1>
        <div v-for="(item) in list" :key="item.id" class="left">
          <h3>{{item.title}}</h3>
          <p v-for="(o) in item.books" :key="o.id">{{o.text}}</p>
        </div>
      </el-col>
      <el-col :span="16" class="right">
        <div class="img"></div>
        <el-col :span="12" v-for="(o) in cards" :key="o.id" class="card">
          <el-card>
            <el-row>
              <el-col :span="8">
                <img
                  src="https://shadow.elemecdn.com/app/element/hamburger.9cf7b091-55e9-11e9-a976-7f4d0b07eef6.png"
                  class="image"
                />
              </el-col>
              <el-col :span="16" class="cardRight">
                <h3>{{o.title}}</h3>
                <p>{{o.verbose}}</p>
                <el-button type="primary" class="button" @click="clickHandle(o.id)">立即购买</el-button>
              </el-col>
            </el-row>
          </el-card>
        </el-col>
      </el-col>
    </el-row>
  </div>
</template>

<script>
export default {
  name: "Main",
  data() {
    return {
      list: [
        {
          id: "dev",
          title: "移动互联网开发专业书籍",
          books: [
            {
              id: "dev1",
              text: "Web标准网站设计之道"
            },
            {
              id: "dev2",
              text: "photoshop商业网站设计"
            },
            {
              id: "dev3",
              text: "c#编程基础"
            },
            {
              id: "dev4",
              text: "SQL server数据库基础"
            },
            {
              id: "dev5",
              text: "c#桌面应用程序开发"
            },
            {
              id: "dev6",
              text: "Java语言基础"
            },
            {
              id: "dev7",
              text: "Java面向对象编程"
            },
            {
              id: "dev8",
              text: "Java语言高级特性"
            }
          ]
        },
        {
          id: "apl",
          title: "移动互联网应用专业书籍",
          books: [
            {
              id: "apl1",
              text: "计算机基础应用"
            },
            {
              id: "apl2",
              text: "Linux系统管理"
            },
            {
              id: "apl3",
              text: "企业网络互联技术"
            },
            {
              id: "apl4",
              text: "Windows网络服务管理"
            },
            {
              id: "apl5",
              text: "Windows系统管理"
            },
            {
              id: "apl6",
              text: "Windows活动目录管理"
            },
            {
              id: "apl7",
              text: "计算机网络技术"
            }
          ]
        }
      ],
      cards: [
        {
          id: "card1",
          title: "移动互联网开发全套书籍",
          verbose: "老八蜜汁汉堡一天三餐少不了"
        },
        {
          id: "card2",
          title: "移动互联网应用全套书籍",
          verbose: "老八蜜汁汉堡一天三餐少不了"
        },
        {
          id: "card3",
          title: "大数据全套书籍",
          verbose: "老八蜜汁汉堡一天三餐少不了"
        },
        {
          id: "card4",
          title: "人工智能全套书籍",
          verbose: "老八蜜汁汉堡一天三餐少不了"
        }
      ]
    };
  },
  methods: {
    clickHandle(id) {
      this.$router.push({
        name: "Detail",
        params: {
          id: id
        }
      });
    }
  }
};
</script>

<style scoped lang="scss">
.home {
  .left {
    background: #ffffff;
    h3 {
      height: 30px;
      line-height: 30px;
    }
    p,
    h3 {
      padding-left: 10px;
    }
  }
  h1 {
    height: 40px;
    line-height: 40px;
    padding-left: 5px;
    background: rgb(177, 155, 197);
  }
  .right {
    background: transparent;
    img {
      width: 100%;
    }
    .card {
      margin-bottom: 5px;
    }
    h3 {
      margin-bottom: 16px;
    }
    p,
    h3 {
      padding-left: 10px;
      text-align: left;
    }
    .cardRight {
      text-align: center;
    }
    .button {
      margin-top: 20px;
    }
  }
  .img {
    height: 200px;
    background: rgb(201, 201, 69);
    margin-bottom: 5px;
  }
}
</style>
