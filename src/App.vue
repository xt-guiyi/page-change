<template>
<table-change :titleSouce="titleInfo">
  <table-pane :activeKey="1">
    <div class="shop-content">
      <goods-card></goods-card>
    </div>
  </table-pane>
  <table-pane :activeKey="2" style="overflow:scroll">
    <div class="shop-content">
      <div>
        <goods-card :data="toBeExchanged"></goods-card>
      </div>
    </div>
  </table-pane>
  <table-pane :activeKey="3" style="overflow:scroll">
    <goods-card :data="converted"></goods-card>

  </table-pane>
  <table-pane :activeKey="4">
    <div class="shop-content" style="overflow:scroll" @scroll.passive="onScroll">
      <div class="scroll-container">
        <goods-card :data="Expired"></goods-card>

      </div>
    </div>
  </table-pane>
  <table-pane :activeKey="5">
    <div class="shop-content">
      <goods-card></goods-card>
    </div>
  </table-pane>
</table-change>
</template>

<script>
import {
  provide,
  reactive,
  ref
} from "vue";
import TableChange from "./components/table/TableChange";
import TablePane from "./components/table/tablePane";
import GoodsCard from "./components/GoodsCard";

export default {
  name: "App",
  components: {
    TableChange,
    TablePane,
    GoodsCard
  },
  setup() {
    // table标题
    const titleInfo = reactive([{
        title: "待付款",
        number: 0
      },
      {
        title: "待兑换",
        number: 2
      },
      {
        title: "已兑换",
        number: 1
      },
      {
        title: "已过期",
        number: 16
      },
      {
        title: "售后退款",
        number: 0
      },
    ]);
    // 假数据1
    const toBeExchanged = reactive([{
        img: '图片',
        title: '商品1号',
        price: 120,
        Discount: '1'

      },
      {
        img: '图片',
        title: '商品2号',
        price: 120,
        Discount: '1'

      },
    ])
    // 假数据2
    const converted = reactive([{
      img: '图片',
      title: '商品1号',
      price: 120,
      Discount: '1'

    }, ])
    // 下拉刷新假数据3
    const Expired = reactive([{
        img: '图片',
        title: '商品1号',
        price: 120,
        Discount: '1'
      },
      {
        img: '图片',
        title: '商品2号',
        price: 120,
        Discount: '1'

      },
      {
        img: '图片',
        title: '商品3号',
        price: 120,
        Discount: '1'

      },
      {
        img: '图片',
        title: '商品4号',
        price: 120,
        Discount: '1'

      },

    ])
    // 提示消息
    const tipsText = ref('加载中...')
    const isTips = ref(false)
    // 提供依赖
    provide('tipsText', tipsText)
    provide('isTips', isTips)

    /**
     * 监听滚动事件实现下拉加载
     */
    const onScroll = function (e) {
      if (e.target.scrollTop + e.target.clientHeight >= e.target.scrollHeight - 0.5) {
        isTips.value = true
        setTimeout(() => {
          // 发ajax得到的假数据
          const newData = [{
              img: '图片',
              title: '商品5号',
              price: 120,
              Discount: '1'

            },
            {
              img: '图片',
              title: '商品6号',
              price: 120,
              Discount: '1'

            },
            {
              img: '图片',
              title: '商品7号',
              price: 120,
              Discount: '1'

            },
            {
              img: '图片',
              title: '商品8号',
              price: 120,
              Discount: '1'

            },
          ]
          Expired.push(...newData)
          isTips.value = false
        }, 2000)

      }
    }

    return {
      titleInfo,
      toBeExchanged,
      converted,
      Expired,
      onScroll,
    }
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app,
body,
html {
  height: 100%;
  overflow: hidden
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background-color: #F8F8FA;
}

.shop-content {
  height: 607px;
  -webkit-overflow-scrolling: touch
}

.scroll-container {}
</style>
