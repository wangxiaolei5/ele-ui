<template>
    <div class="hm-form-item">
        <label class="hm-form-item__label" :style="labelStyle">{{label}}</label>
        <div class="hm-form-item__content">
          <slot></slot>
        </div>
    </div>
</template>
<script>
export default {
  name: 'HmFormItem',
  inject: ['Form'],
  props: {
    label: {
      type: String,
      default: ''
    }
  },
  computed: {
    labelStyle () {
      return {
        width: this.Form.labelWidth
      }
    }
  }
}
</script>
<style lang="scss">
.hm-form-item {
  margin-bottom: 25px;
  .hm-form-item__label {
    text-align: right;
    vertical-align: middle;
    float: left;
    font-size: 14px;
    color: #606266;
    line-height: 40px;
    padding: 0 12px 0 0;
    box-sizing: border-box;
  }
  .hm-form-item__content {
    line-height: 40px;
    position: relative;
    font-size: 14px;
    overflow: hidden;
  }
}
</style>
