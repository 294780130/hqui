<template>
  <div id="app">
    <my-input placeholder="请输入用户名" type="password" name="username" disabled></my-input>
    <my-input v-model="username"></my-input>
    <my-input v-model="username" clearable></my-input>
    <my-input v-model="username" type="password" show-password></my-input>
    <!-- <input type="text" v-model="username"> -->
    <!-- <input type="text" :value="username" @input="username=$event.target.value"> -->
    <hr>
    <my-switch v-model="choosed"></my-switch>
    <my-switch v-model="choosed" active-color="green"></my-switch>
    <hr>
    <my-radio v-model="gender" label="1">男</my-radio>
    <my-radio v-model="gender" label="0">女</my-radio>
    <my-radio v-model="gender" label="1"></my-radio>
    <my-radio v-model="gender" label="0"></my-radio>
    <hr>
    <my-radio-group v-model="gender">
      <my-radio label="1">男</my-radio>
      <my-radio label="0">女</my-radio>
    </my-radio-group>
    <hr>
    <my-checkbox v-model="active">是否选中</my-checkbox>
    <my-checkbox-group v-model="hobby">
      <my-checkbox label="爱好1"></my-checkbox>
      <my-checkbox label="爱好2"></my-checkbox>
      <my-checkbox label="爱好3"></my-checkbox>
    </my-checkbox-group>
    <hr>
    <my-form :model="model">
      <my-form-item label="用户名">
        <my-input placeholder="请输入用户名" v-model="model.username"></my-input>
      </my-form-item>
      <my-form-item label="选择">
        <my-switch v-model="model.active"></my-switch>
      </my-form-item>
    </my-form>
  </div>
</template>

<script>
export default {
  data(){
    return{
      username: '张三',
      choosed: false,
      gender: '1',
      active: false,
      hobby: ['爱好1','爱好2','爱好3'],
      model: {
        username: '',
        active: true
      }
    }
  }
}
</script>

<style lang="scss" scoped>
#app{
  .my-input{
    width: 180px;
  }
}
</style>
