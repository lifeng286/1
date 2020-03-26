<template>
  <div class="login-container">
    <div class="login-box">
      <div class="avatar-box">
        <!-- 头像区域 -->
        <img src="../assets/logo.png" alt="" />
      </div>
      <!-- 登入表单 -->
      <el-form
        ref="loginformref"
        label-width="0px"
        class="login-form"
        :model="form"
        :rules="loginformrules"
      >
        <!-- 用户名 -->
        <el-form-item prop="username">
          <el-input
            v-model="form.name"
            prefix-icon="el-icon-user-solid"
          ></el-input>
        </el-form-item>
        <!-- 密码 -->
        <el-form-item prop="password">
          <el-input
            v-model="form.password"
            prefix-icon="el-icon-user-solid"
            type="password"
          ></el-input>
        </el-form-item>
        <!-- 按钮区 -->
        <el-form-item class="btns">
          <el-button type="primary" @click="login"
            ><router-link to="/home">登入</router-link></el-button
          >
          <el-button type="info" @click="resetloginform"
            ><center>重置</center></el-button
          >
        </el-form-item>
      </el-form>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      form: {
        name: "",
        password: ""
      },
      loginformrules: {
        username: [
          { required: true, message: "请输登入名称", trigger: "blur" },
          { min: 3, max: 5, message: "长度在 3 到 5 个字符", trigger: "blur" }
        ],
        password: [
          { required: true, message: "请输登入密码", trigger: "blur" },
          { min: 6, max: 15, message: "长度在 6 到 15 个字符", trigger: "blur" }
        ]
      }
    };
  },
  methods: {
    resetloginform() {
      //  console.log(this)
      this.$refs.loginformref.resetFields();
    },
    login() {
      this.$refs.loginformref.validate(valid => {
        if (!valid) return;
        // const{data: res}=await this.$http.post("login,this.loginform"),
      });
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

<style scoped>
.login-container {
  background-color: #2b3b6b;
  height: 100%;
}

.login-box {
  width: 450px;
  height: 300px;
  background-color: #fff;
  border-radius: 3px;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.avatar-box {
  height: 130px;
  width: 130px;
  border: 1px solid #eee;
  border-radius: 50%;
  padding: 10px;
  box-shadow: 0 0 10px #ddd;
  position: absolute;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: #fff;
}

.avatar-box img {
  width: 100%;
  height: 100%;
  border-radius: 50%;
  background-color: #eee;
}

.btns {
  display: flex;
  justify-content: flex-end;
}

.login-form {
  position: absolute;
  bottom: 0;
  width: 100%;
  padding: 0 20px;
  box-sizing: border-box;
}
</style>
