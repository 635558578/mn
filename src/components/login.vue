<template>
  <!-- 头部盒子 -->
  <div class="header">
    <!-- 标题区域 -->
    <div class="lnner-header">
      <div>
        <h1>成都东软学院管理网</h1>
        <h2>登录</h2>
        <el-form :rules="rules" class="login-form" ref="form" :model="loginform" @keyup.enter.native="login">
          <el-form-item prop="username">
            <el-input placeholder="请输入账号" type="text" v-model="loginform.username"></el-input>
          </el-form-item>
          <el-form-item prop="password">
            <el-input placeholder="请输入密码" type="password" v-model="loginform.password" show-password></el-input>
          </el-form-item>
          <el-form-item>
            <el-button :loading="loading" type="primary" style="width: 100%" @click="login">登 录</el-button>
          </el-form-item>
           <el-form-item class="forget">
               <router-link
            :to="{ path: '/forget'}"
            replace
          >忘记密码？</router-link>
          </el-form-item>
        </el-form>
      </div>
    </div>
    <!-- 波浪区域 -->
    <div>
      <!-- svg形状 -->
      <svg class="waves" viewBox="0 24 150 28" preserveAspectRatio="none" shape-rendering="auto">
        <!-- 形状容器 -->
        <defs>
          <path id="gentle-wave" d="M-160 44c30 0 58-18 88-18s 58 18 88 18 58-18 88-18 58 18 88 18 v44h-352z" />
        </defs>
        <!-- 组合形状 -->
        <g class="parallax">
          <use xlink:href="#gentle-wave" x="48" y="0" fill="rgba(255,255,255,0.7" />
          <use xlink:href="#gentle-wave" x="48" y="3" fill="rgba(255,255,255,0.5)" />
          <use xlink:href="#gentle-wave" x="48" y="5" fill="rgba(255,255,255,0.3)" />
          <use xlink:href="#gentle-wave" x="48" y="7" fill="#fff" />
        </g>
      </svg>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      loginform: {
        username: '',
        password: ''
      },
      loading: false,
      rules: {
        username: [{ required: true, message: '请输入用户名', trigger: 'biur' }],
        password: [{ required: true, message: '请输入密码', trigger: 'blur' }]
      }
    }
  },
  methods:{
    login(){
       this.$router.push("./home");
    }
  },
  computed: {
    //实现账号密码任意一个未填写，不能点击登录按钮
    // canSubmit(){
    //   const{ username , password } = this.user
    //   return Boolean(username&&password)
    // },
  },
  watch: {},
  created () {},
  mounted () {
    // 实现按下回车键后登录
    var that = this
    document.onkeydown = () => {
      var key = window.event.keyCode
      // console.log(key)  13 是回车键
      if (key === 13) {
        that.onLogin()
      }
    }
  }
}
</script>

<style scoped>
.forget {
    height: 0;
}
.forget a {
  text-decoration: none;
  color: #74b3f1;
  float: right;
}
.header {
position: relative;
background: linear-gradient(60deg,rgba(84,58,183,1) 0%, rgba(0,172,193,1) 100%);
color: wheat;
}
.lnner-header {
height: 500px;
width: 100%;
display: flex;
flex-direction: column;
justify-content: center;
align-items: center;
}
h1{
 text-align: center;
      font-family: 'Lato','sans-serif';
      font-weight: 300;
      /* font-spacing:2px; */
      font-size: 48px;
}
h2{
    text-align: center;
      font-family: 'Lato','sans-serif';
      font-weight: 300;
      /* font-spacing:2px; */
      font-size: 28px;
}
.login-form{
     margin: 0 auto;
      width: 300px;
      padding-top: 30px;
}
.waves {
     position: relative;
    width: 100%;
    height: 15vh;
    margin-bottom: -7px;
    /* 最小值 */
    min-height: 100px;
    /* 最大值 */
    max-height: 150px;
}
.parallax>use {
     animation: move-forever 25s cubic-bezier(.55,.5,.45,.5) infinite;
}
.parallax>use:nth-child(1) {
    /* 延迟 2s 执行 */
      animation-delay: -2s;
      /* 7s 内 执行完毕 */
      animation-duration: 7s;
}
.parallax>use:nth-child(2) {
      animation-delay: -3s;
      animation-duration: 10s;
    }
    .parallax>use:nth-child(3) {
      animation-delay: -4s;
      animation-duration: 13s;
    }
    .parallax>use:nth-child(4) {
      animation-delay: -5s;
      animation-duration: 20s;
    }
@keyframes move-forever {
    0%{
        transform: translate3d(-90px,0,0);
    }
    100%{
        transform: translate3d(85px,0,0);
    }
}
@media (max-width:768px) {
    .waves{
        height: 40px;
        min-height: 40px;
    }
    h1{
        font-size: 24px;
    }
}
.el-input__inner{
     background-color: rgba(255,255,255,0.7);
  border-radius: 0;
  border: 1px solid #0094ff;
  color: rgba(0, 0, 0, .7)
}
.el-input__inner::placeholder {
  color: rgba(0, 0, 0, .3)
}
.el-button {
  border-radius: 4px;
}
</style>
