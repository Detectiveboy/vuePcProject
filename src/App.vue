<template>
  <div id="app">
    <el-container>
      <el-header>
        <el-row :gutter="20">
          <el-col :span="16">
            <div class="grid-content bg-purple logo">格莱书城</div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content bg-purple link">
              <el-link @click="logoIn = true">登录</el-link>
              <el-dialog title="登录" :visible.sync="logoIn">
                <el-form :model="logoInform" class="rejester">
                  <el-form-item label="账号" :label-width="formLabelWidth">
                    <el-input v-model="logoInform.acount" autocomplete="off"></el-input>
                  </el-form-item>
                  <el-form-item label="密码" :label-width="formLabelWidth">
                    <el-input v-model="logoInform.password" autocomplete="off"></el-input>
                  </el-form-item>
                  <el-button type="success">登录</el-button>
                </el-form>
              </el-dialog>
              <el-link @click="rejester = true">注册</el-link>
              <el-dialog title="注册" :visible.sync="rejester">
                <el-form :model="rejesterform" class="rejester">
                  <el-form-item label="账号" :label-width="formLabelWidth">
                    <el-input v-model="rejesterform.acount" autocomplete="off"></el-input>
                  </el-form-item>
                  <el-form-item label="密码" :label-width="formLabelWidth">
                    <el-input v-model="rejesterform.password" autocomplete="off"></el-input>
                  </el-form-item>
                  <el-form-item label="确认密码" :label-width="formLabelWidth">
                    <el-input v-model="rejesterform.surePass" autocomplete="off"></el-input>
                  </el-form-item>
                  <el-button type="success">注册</el-button>
                </el-form>
              </el-dialog>
              <el-link @click="dialogVisible=true">关于</el-link>
              <el-dialog title="关于" :visible.sync="dialogVisible" width="30%">
                <p>在人群之中寻觅着你，就彷佛在海边掬起所有的沙粒， 急于发现你的踪迹，如果不从愿，但愿还有来生。</p>
              </el-dialog>
            </div>
          </el-col>
        </el-row>
      </el-header>
      <el-main>
        <router-view />
      </el-main>
      <el-footer>©版权归私有</el-footer>
    </el-container>
  </div>
</template>
<script>
export default {
  data() {
    return {
      logoIn: false,
      rejester: false,
      dialogVisible: false,
      logoInform: {
        acount: "",
        password: ""
      },
      rejesterform: {
        acount: "",
        password: "",
        surePass: ""
      },
      formLabelWidth: "120px"
    };
  }
};
</script>
<style lang="scss">
* {
  margin: 0;
  padding: 0;
}

body,
html {
  width: 100%;
  height: 100%;
}
#app {
  height: 100%;
  section {
    height: 100%;
  }
  .el-header {
    background: rgb(60, 60, 214);
    .rejester {
      text-align: right;
    }
    .el-dialog__body {
      text-align: left;
    }
    .logo {
      line-height: 60px;
      font-size: 40px;
      color: #ffffff;
    }
    .link {
      text-align: right;
    }
    a {
      color: rgb(132, 132, 146);
      text-decoration: underline;
      line-height: 60px;
      margin-right: 10px;
    }
    .el-form-item__label {
      text-align: center;
    }
    .el-dialog__header {
      text-align: left;
    }
  }
  .el-footer {
    background: rgb(201, 201, 206);
    line-height: 60px;
    text-align: center;
  }
  .el-main{
    background: rgb(222, 217, 228);
  }
}
</style>
