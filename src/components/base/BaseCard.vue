<script>
// 基础卡片
import {
  h
} from 'vue'
export default {
  name: 'BaseCard',
  setup(props, context) {
    return () => h('div', {
      class: 'card-container'
    }, context.slots.default())
  }
}
</script>

<style lang="scss">
.card-container {
  margin: 10px 10px 0 10px;
  background-color: white;
}
</style>
