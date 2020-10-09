<template>
<div id="table-container">
  <div class="table-main" @click="tableChange">
    <div class="table-items" v-for="( item, index ) of titleSouce" :class="[ index === currentItem - 1? 'active-table' : '' ]" :key="index" :data-key="++index">
      <div class="table-title">{{ item.title }}</div>
      <div class="table-number">({{ item.number }})</div>
    </div>
  </div>
</div>
<slot></slot>
</template>

<script>
import {
  provide,
  ref
} from 'vue';
export default {
  name: "TableChange",
  props: {
    // 数据源
    titleSouce: {
      type: Array,
      required: true,
    },
    // 默认项
    defaultItem: {
      type: Number,
      default: 1,
    },
  },
  setup(props) {
    const currentItem = ref(props.defaultItem)
    // console.log(currentItem)
    const tableChange = function (e) {
      let keyValue = e.target.parentNode.dataset.key ? e.target.parentNode.dataset.key : e.target.dataset.key
      currentItem.value = keyValue
      console.log(currentItem)
    }
    provide('currentItem', currentItem)
    return {
      currentItem,
      tableChange
    }

  }
};
</script>

<style lang="scss" scoped>
#table-container {
  height: 60px;
  text-align: center;
  background-color: white;
}

.table-main {
  height: 100%;
  color: #919191;
  display: flex;

  .table-items {
    flex: auto;
    display: flex;
    flex-direction: column;
    justify-content: center;
    position: relative;
  }
}

.active-table {
  color: #E8514A;

  &::after {
    content: "";
    background-color: red;
    height: 4px;
    width: 100%;
    position: absolute;
    left: 0;
    bottom: 0;
  }

}
</style>
