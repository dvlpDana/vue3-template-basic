<template>
  <!-- 부모로부터 상속받고자 하는 부분을 v-bind="$attrs"로 명시적으로 정의 -->
  <div
    v-bind="$attrs"
    class="btn"
    @click="hello">
    <slot></slot>
  </div>
</template>

<script>
import { onMounted } from 'vue'

export default {
  //최상위 요소가 2개 이상일 경우를 고려하여, 자동 상속 받지 않겠다는 의미
  inheritAttrs: false,
  props: {
    color: {
      type: String,
      default: 'gray'
    }
  },
  //hello라는 이벤트 명시적으로 정의
  emits: ['hello'],
  
  // mounted() {
  //   console.log(this.color)
  //   console.log(this.$attrs)
  // },

  // methods: {
  //   hello() {
  //     this.$emit('hello')
  //   }
  // },
  setup(props, context) {
    function hello() {
      context.emit('hello')
    }
    onMounted(() => {
      // props 매개변수에는 props의 데이터들을 받아옴
      console.log(props.color)
      // context 매개변수에는 $사인이 없는 attrs라는 상속받은 모든 속성을 받아옴
      console.log(context.attrs)
    })

    return {
      hello
    }
  }
}
</script>