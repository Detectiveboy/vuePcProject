<template>
  <div>
    <el-row :gutter="20">
      <el-col :span="4" class="left">
        <div :class="cls"></div>
        <p v-for="item in list" :key="item.id" :class="id===item.id? 'active':'p'">{{item.name}}</p>
      </el-col>
      <el-col :span="18" class="right">
        <h1>{{name}}</h1>
        <h3>为了突破普通教学课本，推出以下教学课本</h3>
        <el-form ref="form" :model="form">
          书籍名称：
          <el-radio-group v-model="form.name" @change="changeHandle">
            <el-radio-button v-for="item in this.books" :key="item.id" :label="item.name"></el-radio-button>
          </el-radio-group>
          <br />购买数量：
          <el-input-number v-model="form.num" :min="0"></el-input-number>
          <br />适用校区：
          <el-select v-model="form.school" placeholder="请选择">
            <el-option
              v-for="item in schools"
              :key="item.value"
              :label="item.label"
              :value="item.value"
            ></el-option>
          </el-select>
          <p>总价：{{price}}</p>
          <el-button type="primary" @click="clickHandle">立即购买</el-button>
          <el-dialog :visible.sync="dialogTableVisible">
            <el-table :data="gridData" border>
              <el-table-column property="name" label="书籍名称" width="150"></el-table-column>
              <el-table-column property="num" label="购买数量" width="200"></el-table-column>
              <el-table-column property="school" label="适用校区" width="200"></el-table-column>
              <el-table-column label="总价">
                <template slot-scope="scope">
                  <span>{{scope.row.num*scope.row.price}}</span>
                </template>
              </el-table-column>
            </el-table>
            <el-button type="primary">购买</el-button>
          </el-dialog>
        </el-form>
        <div>
          <h2>书籍简介</h2>
          <p>{{text}}</p>
        </div>
      </el-col>
    </el-row>
  </div>
</template>
<script>
export default {
  data() {
    return {
      id: "",
      name: "",
      books: [],
      text: "",
      cls: ["", "def"],
      form: {
        name: "",
        num: 0,
        price: 0,
        school: ""
      },
      list: [
        {
          id: "card1",
          name: "移动互联网开发书籍",
          cls: "el-icon-s-help",
          books: [
            {
              id: "01",
              name: "c#编程基础",
              text:
                "在人群之中寻觅着你，就彷佛在海边掬起所有的沙粒， 急于发现你的踪迹，如果不从愿，但愿还有来生。",
              price: 30
            },
            {
              id: "02",
              name: "java语言基础",
              text:
                "在人群之中寻觅着你，就彷佛在海边掬起所有的沙粒， 急于发现你的踪迹，如果不从愿，但愿还有来生。",
              price: 35
            },
            {
              id: "03",
              name: "c#桌面应用程序开发",
              text:
                "在人群之中寻觅着你，就彷佛在海边掬起所有的沙粒， 急于发现你的踪迹，如果不从愿，但愿还有来生。",
              price: 25
            }
          ]
        },
        {
          id: "card2",
          name: "移动互联网应用书籍",
          cls: "el-icon-help",
          books: [
            {
              id: "01",
              name: "计算机基础应用",
              text:
                "在人群之中寻觅着你，就彷佛在海边掬起所有的沙粒， 急于发现你的踪迹，如果不从愿，但愿还有来生。",
              price: 30
            },
            {
              id: "02",
              name: "Linux系统管理",
              text:
                "在人群之中寻觅着你，就彷佛在海边掬起所有的沙粒， 急于发现你的踪迹，如果不从愿，但愿还有来生。",
              price: 35
            },
            {
              id: "03",
              name: "企业网络互联技术",
              text:
                "在人群之中寻觅着你，就彷佛在海边掬起所有的沙粒， 急于发现你的踪迹，如果不从愿，但愿还有来生。",
              price: 25
            }
          ]
        },
        {
          id: "card3",
          name: "大数据数据",
          cls: "el-icon-upload",
          books: [
            {
              id: "01",
              name: "Windows系统管理",
              text:
                "在人群之中寻觅着你，就彷佛在海边掬起所有的沙粒， 急于发现你的踪迹，如果不从愿，但愿还有来生。",
              price: 30
            },
            {
              id: "02",
              name: "Windows活动目录管理",
              text:
                "在人群之中寻觅着你，就彷佛在海边掬起所有的沙粒， 急于发现你的踪迹，如果不从愿，但愿还有来生。",
              price: 35
            },
            {
              id: "03",
              name: "计算机网络技术",
              text:
                "在人群之中寻觅着你，就彷佛在海边掬起所有的沙粒， 急于发现你的踪迹，如果不从愿，但愿还有来生。",
              price: 25
            }
          ]
        },
        {
          id: "card4",
          name: "人工智能书籍",
          cls: "el-icon-s-opportunity",
          books: [
            {
              id: "01",
              name: "Java语言基础",
              text:
                "在人群之中寻觅着你，就彷佛在海边掬起所有的沙粒， 急于发现你的踪迹，如果不从愿，但愿还有来生。",
              price: 30
            },
            {
              id: "02",
              name: "Java面向对象编程",
              text:
                "在人群之中寻觅着你，就彷佛在海边掬起所有的沙粒， 急于发现你的踪迹，如果不从愿，但愿还有来生。",
              price: 35
            },
            {
              id: "03",
              name: "Java语言高级特性",
              text:
                "在人群之中寻觅着你，就彷佛在海边掬起所有的沙粒， 急于发现你的踪迹，如果不从愿，但愿还有来生。",
              price: 25
            }
          ]
        }
      ],
      schools: [
        {
          value: "清华大学",
          label: "清华大学"
        },
        {
          value: "北京大学",
          label: "北京大学"
        },
        {
          value: "北京理工",
          label: "北京理工"
        },
        {
          value: "中山大学",
          label: "中山大学"
        },
        {
          value: "南阳农职院",
          label: "南阳农职院"
        }
      ],
      dialogTableVisible: false,
      gridData: []
    };
  },
  computed: {
    price() {
      return this.form.num * this.form.price;
    }
  },
  watch: {
    dialogTableVisible(newVal) {
      if (!newVal) this.gridData = [];
    }
  },
  methods: {
    changeHandle() {
      for (const item of this.books) {
        if (this.form.name === item.name) {
          this.form.price = item.price;
          this.text = item.text;
          break;
        }
      }
    },
    clickHandle() {
      this.dialogTableVisible = true;
      this.gridData.push(this.form);
    }
  },
  beforeMount() {
    const id = this.$route.params.id;
    for (const item of this.list) {
      if (id === item.id) {
        this.cls[0] = item.cls;
        this.id = id;
        this.name = item.name;
        this.books = item.books;
        break;
      }
    }
  },
  mounted() {
    const elleft = document.getElementsByClassName("left")[0];
    const elright = document.getElementsByClassName("right")[0];
    elleft.style = "padding:0";
    elright.style = "padding:0";
  }
};
</script>
<style lang="scss" scoped>
.left {
  background: #ffffff;
  .def {
    width: 100%;
    height: 150px;
    text-align: center;
    line-height: 150px;
    font-size: 100px;
  }
  .p {
    height: 40px;
    line-height: 40px;
    font-size: 20px;
  }
  .active {
    height: 40px;
    line-height: 40px;
    font-size: 20px;
    background: rgb(151, 184, 228);
  }
}
.right {
  background: #ffffff;
  margin-left: 10px;
  h1 {
    height: 50px;
    line-height: 50px;
    padding-left: 10px;
  }
  h3 {
    height: 40px;
    line-height: 40px;
    padding-left: 10px;
    background: rgb(233, 205, 169);
  }
  .el-form {
    padding: 30px 0 30px 20px;
  }
  .el-input-number,
  .el-select {
    margin-top: 10px;
  }
  p,
  .el-button {
    margin-top: 10px;
    margin-left: 30px;
  }
}
</style>