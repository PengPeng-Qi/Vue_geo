<template>
    <div class="login_contaioner">
        <div class="login_box">
            <!-- 登陆表单区域 -->
            <el-form ref="loginFormRef" :model="loginForm" :rules="loginFormRules" label-width="0px" class="login_form">
                <!-- 用户名 -->
                <el-form-item prop="username">
                    <el-input v-model="loginForm.username" placeholder="账号" prefix-icon="iconfont icon-user" style="width: 200px;"></el-input>
                </el-form-item>
                <!-- 密码 -->
                <el-form-item prop="password">
                    <el-input type="password" v-model="loginForm.password" placeholder="密码" prefix-icon="iconfont icon-3702mima" style="width: 200px;"></el-input>
                </el-form-item>
                <!-- 按钮区域 -->
                <el-form-item class="btns">
                    <el-button type="success" round id="button_1" @click="login">登录</el-button>
                </el-form-item>
            </el-form>
        </div>
    </div>
</template>

<script>
export default {
  data () {
    return {
      // 登录表单绑定的数据对象
      loginForm: {
        username: 'admin',
        password: '123456'
      },
      // 表单验证规则对象
      loginFormRules: {
        // 验证用户名是否合法
        username: [
          { required: true, message: '请输入登录名称', trigger: 'blur' },
          { min: 3, max: 10, message: '长度在 3 到 10 个字符', trigger: 'blur' }
        ],
        // 验证密码是否合法
        password: [
          { required: true, message: '请输入登录密码', trigger: 'blur' },
          { min: 6, max: 15, message: '长度在 6 到 15 个字符', trigger: 'blur' }
        ]
      }
    }
  },
  methods: {
    login () {
      this.$refs.loginFormRef.validate(async valid => {
        if (!valid) return
        const { data: res } = await this.$http.post('login', this.loginForm)
        if (res.meta.status !== 200) return this.$message.error('登录失败')
        this.$message.success('登录成功')
        // 1. 将登录成功之后的 token，保存到客户端的 sessionStorage 中
        //   1.1 项目中出了登录之外的其他API接口，必须在登录之后才能访问
        //   1.2 token 只应在当前网站打开期间生效，所以将 token 保存在 sessionStorage 中
        window.sessionStorage.setItem('token', res.data.token)
        // 2. 通过编程式导航跳转到后台主页，路由地址是 /home
        this.$router.push('/home')
      })
    }
  }
}
</script>

<style Lang="less" scoped>
/*
body {
    background-image: url("../assets/YunNan.PNG");
}
*/
.login_contaioner {
    background-color: #2f4f6f;
    height: 100%;
}

.login_box {
    height: 300px;
    width: 450px;
    background-color: #fff;
    border-radius: 27px;
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
}

.login_form {
    position: absolute;
    right: 20px;
    top: 70px;
    width: 45%;
    padding: 0 20px 0px 0px;
    box-sizing: border-box;
/*
    border: 1px #000 solid;
*/
}
.btns {
    display: flex;
    justify-content: center;
}

#button_1 {
    font-size: 10px;
    height: 25px;
    width: 100px;
    background-color: #02866E;
    padding-top: 5px;
}

</style>
