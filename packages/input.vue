<template>
    <div class="hm-input hm-input--suffix" :class="{'hm-input--suffix':showSuffix}">
        <input class="hm-input__inner" :class = "{'is-disabled': disabled}"
               :type="showPassword ? (passwordVisible ? 'text':'password') : type "
               :placeholder="placeholder"
               :name= "name"
               :value= "value"
               @input= "handleInput"
        >
        <span class="hm-input__suffix" v-if="showSuffix">
          <i class="hm-input__icon hm-icon-circle-close" v-if="clearable && value" @click="clrear"></i>
          <i class="hm-input__icon hm-icon-view" v-if="showPassword" @click="handlePassword"
             :class="{'hm-icon-view-active': passwordVisible}"></i>
        </span>
    </div>
</template>
<script>
export default {
  name: 'HmInput',
  data () {
    return {
      passwordVisible: false
    }
  },
  props: {
    placeholder: {
      type: String,
      default: ''
    },
    type: {
      type: String,
      default: 'text'
    },
    name: {
      type: String,
      default: ''
    },
    disabled: {
      type: Boolean,
      default: false
    },
    value: {
      type: String,
      default: ''
    },
    clearable: {
      type: Boolean,
      default: false
    },
    showPassword: {
      type: Boolean,
      default: false
    }
  },
  computed: {
    showSuffix () {
      return this.clearable || this.showPassword
    }
  },
  methods: {
    handleInput (e) {
      this.$emit('input', e.target.value)
    },
    clrear () {
      this.$emit('input', '')
    },
    handlePassword () {
      this.passwordVisible = !this.passwordVisible
    }
  }
}
</script>
<style lang="scss">
.hm-input {
  width: 180px;
  position: relative;
  font-size: 14px;
  display: inline-block;
  .hm-input__inner {
    cursor: pointer;
    -webkit-appearance: none;
    background-color: #fff;
    background-image: none;
    border-radius: 4px;
    border: 1px solid #dcdfe6;
    box-sizing: border-box;
    color: #000;
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
.hm-input--suffix {
  .hm-input__inner {
    padding-right: 30px;
  }
  .hm-input__suffix {
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
      &.hm-icon-view-active {
        color: blue
      }
    }
  }
}
</style>
