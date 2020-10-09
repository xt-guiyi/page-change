<template>
<base-card class="card-padding" v-for="(item , index) of data" :key="index">
  <base-goods-exhibition :goodsSouce="item"></base-goods-exhibition>
  <base-one-px></base-one-px>
  <fold-card>
    <fold-card-item title="微信支付">微信支付</fold-card-item>
    <fold-card-item title="支付宝支付">支付宝支付</fold-card-item>
    <fold-card-item title="本地玩支付">本地玩支付</fold-card-item>
  </fold-card>
  <div class="seeOrder">查看订单</div>
</base-card>
<div v-show="isTips" class="tips">{{ tipsText }}</div>
</template>

<script>
import {
  inject
} from 'vue';
import BaseCard from "./base/BaseCard";
import BaseGoodsExhibition from "./base/BaseGoodsExhibition";
import BaseOnePx from "./base/BaseOnePx";
import FoldCard from "./fold/FoldCard";
import FoldCardItem from "./fold/FoldCardItem";
export default {
  name: 'GoodsCard',
  props: {
    data: {
      type: Object,
      required: true
    },
  },
  components: {
    BaseCard,
    BaseGoodsExhibition,
    BaseOnePx,
    FoldCard,
    FoldCardItem
  },
  setup() {
    const tipsText = inject('tipsText')
    const isTips = inject('isTips')
    return {
      tipsText,
      isTips
    }
  }
}
</script>

<style lang="scss" scoped>
.card-padding {
  padding: 10px;
}

.seeOrder {
  width: 80px;
  height: 30px;
  line-height: 30px;
  text-align: center;
  border-radius: 25px;
  border: 1px solid red;
  margin: 10px 0px 0px 250px;

}

.tips {
  height: 40px;
  line-height: 40px;
  font-size: 20px;
  text-align: center;
  margin: 0px 10px 0 10px;
  background-color: white;

}
</style>
