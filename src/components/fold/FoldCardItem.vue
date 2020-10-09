<template>
<div class="card-item">
  <slot></slot>
</div>
</template>

<script>
// 折叠项组件
export default {
  name: 'FoldCardItem',
  props: {
    title: {
      type: String,
      required: true
    }
  }
}
</script>

<style lang="scss" scoped>
.card-item {
  height: 35px;
  line-height: 35px;
  border-top: 1px solid rgb(240, 238, 238);
  font-size: 12px;
}
</style>
