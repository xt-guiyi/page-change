<script>
// 1px组件
import {
  h
} from 'vue'
export default {
  name: 'BaseCard',
  setup() {
    return () => h('div', {
      class: 'set-one-px'
    })
  }
}
</script>

<style lang="scss">
.set-one-px {
  position: relative;
  padding: 10px;

  &::after {
    position: absolute;
    content: "";
    background-color: #e5e5e5;

    display: block;
    width: 100%;
    height: 1px;
    /*no*/
    transform: scale(1, 0.5);
    left: 0;
  }
}
</style>
