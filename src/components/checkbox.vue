<template>
  <div class="vava-checkbox" :class="{'is-round': round}"><span @click="handleCheck" class="vava-checkbox-select" :class="{active: currentValue}"><i class="icon icon-selected"></i></span><slot></slot></div>
</template>

<script>
  export default {
    name: 'VavaCheckbox',
    componentName: 'VavaCheckbox',
    props: {
      value: Boolean,
      round: Boolean
    },
    watch: {
      value (newValue) {
        this.currentValue = newValue
      }
    },
    data () {
      return {
        currentValue: this.value
      }
    },
    methods: {
      handleCheck () {
        this.currentValue = !this.currentValue
        this.$emit('input', this.currentValue)
        this.$emit('change', this.changeValue)
      }
    }
  }
</script>

<style lang="less" scoped>
  .vava-checkbox{
    display: flex;
    flex-wrap: nowrap;
    align-items: center;
    color: #666;
    line-height: 1.3;
    .vava-checkbox-select{
      display: flex;
      width: 1.6vw;
      height: 1.6vw;
      min-width: 20px;
      min-height: 20px;
      align-items: center;
      justify-content: center;
      margin-right: 1.04vw;
      background-color: #666;
      transition: .3s all;
      flex-shrink: 0;
      border-radius: 2px;
      cursor: pointer;
      i{
        color: #FFF;
        font-size: 0.6vw;
      }
    }
    span.active{
      background-color: #009688;
    }
  }
  .is-round{
    .vava-checkbox-select{
      background-color: #FFF;
      border: 1px solid #666;
      width: 1.25vw;
      height: 1.25vw;
      border-radius: 50%;
    }
  }
  @media (max-width: 1350px) {
    .vava-checkbox{
      .vava-checkbox-select{
        margin-right: 15px;
        i{
          font-size: 10px;
        }
      }
    }
    .is-round{
      .vava-checkbox-select{
        i{
          font-size: 9px;
        }
      }
    }
  }
  @media (max-width: 500px) {
  }
</style>
