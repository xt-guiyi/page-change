<template>
<div class="goods-container">
  <div class="goods-img">{{ goodsSouce.img }}</div>
  <div class="goods-detailed">
    <div class="top">{{ goodsSouce.title }}</div>
    <div class="center">商品单价：￥{{ goodsSouce.price }}</div>
    <div class="bottom">抵扣金折扣：￥{{ goodsSouce.Discount }}</div>
  </div>
</div>
</template>

<script>
// 商品展示栏组件
export default {
  name: 'BaseGoodsExhibition',
  props: {
    goodsSouce: {
      type: Object,
      required: true
    }
  }

}
</script>

<style lang="scss" scoped>
.goods-container {
  display: flex;

  .goods-img {
    width: 100px;
    height: 100px;
    line-height: 100px;
    text-align: center;
    background-color: grey;
    border-radius: 5%;
  }

  .goods-detailed {
    text-indent: 10px;
    display: flex;
    flex-direction: column;
    justify-content: space-around;

    .bottom {
      color: #E74E45;
    }
  }
}
</style>
