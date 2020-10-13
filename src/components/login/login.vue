<template>
  <div class="login-wrap">
    <el-form class="login-form" ref="form" :model="form" label-width="80px" label-position="top">
      <h2>登录</h2>
      <el-form-item label="用户名">
        <el-input v-model="form.username"></el-input>
      </el-form-item>
      <el-form-item label="密码">
        <el-input v-model="form.password"></el-input>
      </el-form-item>
      <el-form-item>
        <el-button class="login-btn" type="primary" @click.prevent="handelLogin">登录</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
export default {
  name: 'Login',
  data () {
    return {
      form: {
        username: '',
        password: ''
      }
    }
  },
  methods: {
    handelLogin () {
      this.$http.post('login', this.form).then(res => {
        // console.log(res)
        // console.log(res)
        // const {
        //   meta: {msg, status}
        // } = res.data
        // 添加弹框
        // 如果成功
        // localStorage.setItem('token', data.token)
        this.$router.push({name: 'home'})
        this.$message.success('登录成功')
        // if (status === 200) {
        //   this.$router.push({name: 'home'})
        //   this.$message.success(msg)
        // } else {
        //   this.$message.warning(msg)
        // }
      })
    }
  }
}

</script>

<style>
.login-wrap {
  height: 100%;
  background-color: #324154;
  display: flex;
  align-items: center;
  justify-content: center;
}

.login-form {
  width: 400px;
  background-color: #fff;
  border-radius: 5px;
  padding: 20px;
}

.login-btn {
  width: 100%;
}
</style>
