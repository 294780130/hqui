<template>
  <div class="my-input" :class="{'my-input--suffix': showSuffix}">
    <input
        :type="showPassword ? (passwordVisible ? 'text' : 'password') : type"
        class="my-input__inner"
        :class="{'is-disabled': disabled}"
        :placeholder="placeholder"
        :name="name"
        :disabled="disabled"
        :value="value"
        @input="handleInput"
    >
    <span class="my-input__suffix" v-if="showSuffix">
        <i class="my-input__icon my-icon-circle-close" v-if="clearable && value" @click="clear"></i>
        <i class="my-input__icon my-icon-view" v-if="showPassword" @click="handlePassword" :class="{'my-icon-view-active':passwordVisible}"></i>
    </span>
  </div>
</template>

<script>
export default {
    name: 'MyInput',
    props:{
        placeholder:{
            type: String,
            default: ''
        },
        type:{
            type: String,
            default: 'text'
        },
        name:{
            type: String,
            default: ''
        },
        disabled:{
            type: Boolean,
            default: false
        },
        value: {
            type: String,
            default: ''
        },
        clearable:{
            type: Boolean,
            default: false
        },
        showPassword: {
            type: Boolean,
            default: false
        }
    },
    data(){
        return{
            // 控制是否显示密码框
            passwordVisible: false
        }
    },
    computed:{
        showSuffix(){
            return this.clearable || this.showPassword;
        }
    },
    methods:{
        handleInput(e){
            this.$emit('input', e.target.value)
        },
        clear(){
            this.$emit('input', '')
        },
        handlePassword(){
            this.passwordVisible = !this.passwordVisible;
        }
    }
}
</script>

<style lang="scss" scoped>
.my-input {
  width: 100%;
  position: relative;
  font-size: 14px;
  display: inline-block;
  .my-input__inner {
    -webkit-appearance: none;
    background-color: #fff;
    background-image: none;
    border-radius: 4px;
    border: 1px solid #dcdfe6;
    box-sizing: border-box;
    color: #606266;
    display: inline-block;
    font-size: inherit;
    height: 40px;
    line-height: 40px;
    outline: none;
    padding: 0 15px;
    transition: border-color .2s cubic-bezier(.645,.045,.355,1);
    width: 100%;

    &:focus {
      outline: none;
      border-color: #409eff;
    }
    &.is-disabled {
      background-color: #f5f7fa;
      border-color: #e4e7ed;
      color: #c0c4cc;
      cursor: not-allowed;
    }
  }
}

.my-input--suffix {
  .my-input__inner {
    padding-right: 30px;
  }
  .my-input__suffix {
    position: absolute;
    height: 100%;
    right: 10px;
    top: 0;
    line-height: 40px;
    text-align: center;
    color: #c0c4cc;
    transition: all .3s;
    z-index: 900;
    i {
      color: #c0c4cc;
      font-size: 14px;
      cursor: pointer;
      transition: color .2s cubic-bezier(.645,.045,.355,1);
    }
    .my-icon-view-active {
      color: blue;
    }
  }

}
</style>