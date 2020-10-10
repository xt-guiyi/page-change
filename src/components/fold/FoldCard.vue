<template>
<div id="fold-card-container">
  <div class="card-cell" @click="openPayWay">
    <div class="card-cell-title">支付方式</div>
    <i :class="[isShow? 'arrow-rotate' :'']"></i>
  </div>

  <div ref="itemRefs" class="card-content" style="height: 0px">
    <slot></slot>
  </div>
</div>
</template>

<script>
// 折叠组件
import {
  ref
} from 'vue'
export default {
  name: 'FoldCard',
  setup() {
    const isShow = ref(false)
    const itemRefs = ref(null)
    const openPayWay = function () {
      // 实现渐变
      if (itemRefs.value.style.height === '0px') {
        itemRefs.value.removeAttribute("style");
        isShow.value = true
      } else {
        itemRefs.value.setAttribute("style", 'height: 0px')
        isShow.value = false
      }
    }
    return {
      isShow,
      openPayWay,
      itemRefs
    }
  }
}
</script>

<style lang="scss" scoped>
#fold-card-container {

  .card-cell {
    height: 40px;
    line-height: 40px;
    color: #323233;
    font-size: 14 px;
    display: flex;
    justify-content: space-between;
  }

  i {
    position: relative;
    display: inline-block;
    width: 40px;
    background-image: url('../../assets/img/downArrow.svg');
    background-repeat: no-repeat;
    background-position: center;
    background-size: 55%;
    transition: transform 0.5s ease;
  }
}

.arrow-rotate {
  transform: rotate(-180deg);
}

.card-content {
  height: 105px;
  overflow: hidden;
  transition: height 0.3s ease-in-out
}
</style>
