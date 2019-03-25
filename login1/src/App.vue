<template>
  <Form ref="formInline" :model="formInline" :rules="ruleInline" inline>
      <FormItem prop="user">
          <Input type="text" v-model="formInline.user" placeholder="用户名">
              <Icon type="ios-person-outline" slot="prepend"></Icon>
          </Input>
      </FormItem>
      <FormItem prop="password">
          <Input type="password" v-model="formInline.password" placeholder="密码">
              <Icon type="ios-lock-outline" slot="prepend"></Icon>
          </Input>
      </FormItem>
      <FormItem class="singin">
          <Button type="primary" @click="handleSubmit('formInline')">登录</Button>
      </FormItem>
  </Form>
</template>
<script>
  export default {
      data () {
          return {
              formInline: {
                  user: '',
                  password: ''
              },
              ruleInline: {
                  user: [
                      { required: true, message: '请填写用户名', trigger: 'blur' }
                  ],
                  password: [
                      { required: true, message: '请填写密码', trigger: 'blur' },
                      { type: 'string', min: 6, message: '密码长度不能小于6位', trigger: 'blur' }
                  ]
              }
          }
      },
      methods: {
          handleSubmit(name) {
              this.$refs[name].validate((valid) => {
                  if (valid) {
                      this.$Message.success('Success!');
                  } else {
                      this.$Message.error('Fail!');
                  }
              })
          }
      }
  }
</script>
<style>
.ivu-form{
  margin-top: 50%;
}

.ivu-form-item{
  width: 100%;
}

.ivu-form-item-content{
  width: 50%;
  margin: 0 auto;
}

.ivu-form-item-content{
  text-align: center;
}
</style>