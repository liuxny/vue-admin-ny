<template>
    <div class="login">
            <div class="login-con">
                <Card>
                    <p slot="title">
                        <Icon type="log-in"></Icon>
                        欢迎登录
                    </p>
                    <div class="form-con">
                        <Form>
                            <FormItem>
                                <Input v-model="form.userName" placeholder="请输入用户名">
                                    <span slot="prepend">
                                        <Icon :size="16" type="person"></Icon>
                                    </span>
                                </Input>
                            </FormItem>
                            <FormItem prop="password">
                                <Input v-model="form.userName" type="password" placeholder="请输入密码">
                                    <span slot="prepend">
                                        <Icon :size="14" type="locked"></Icon>
                                    </span>
                                </Input>
                            </FormItem>
                            <FormItem>
                                <Button @click="handleSubmit" type="primary" long>登录</Button>
                            </FormItem>
                        </Form>
                        <p class="login-tip">输入任意用户名和密码即可</p>
                    </div>
                </Card>
            </div>
        </div>
</template>
<script>
export default {
  name: 'Login',
  data () {
    return {
      form: {
        userName: '',
        password: ''
      },
      rules: {
        userName: [
          { required: true, message: '账号不能为空', trigger: 'blur' }
        ],
        password: [
          { required: true, message: '密码不能为空', trigger: 'blur' }
        ]
      }
    };
  },
  methods: {
    handleSubmit () {
      this.$refs.loginForm.validate((valid) => {
        if (valid) {
          localStorage.set('user', this.form.userName);
          localStorage.set('password', this.form.password);
          this.$router.push({path: 'Index'});
        }
      })
    }
  }
}
</script>

<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

.login{
    width: 100%;
    height: 100%;
    background-color:#ccc776;
    background-size: cover;
    background-position: center;
    position: relative;
}
.login-con{
    position: absolute;
    top: 50%;
    left:50%;
    transform: translate(-50%,-50%);
    width: 300px;
}
.login-header{
    font-size: 16px;
    font-weight: 300;
    text-align: center;
    padding: 30px 0;
}
.form-con{
    padding: 10px 0 0;
}
.login-tip{
    font-size: 10px;
    text-align: center;
    color: #c3c3c3;
}
</style>
