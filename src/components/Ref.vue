<template>
  <!-- reference : 참조, 해당하는 특정 요소를 'hello'라는 이름으로 참조하겠다는 의미 -->
  <Hello ref="hello" />
</template>

<script>
import Hello from "~/components/Hello";
export default {
  components: {
    Hello
  },
  // ref와 같은 속성은 컴포넌트가 html 구조와 연결이 된 직후에만 사용할 수 있음, 때문에 created라는 라이프사이클에서는 활용할 수 없음
  created() {
    console.log(this.$refs.hello);
  },
  mounted() {
    // const h1El = document.querySelector('h1')
    console.log(this.$refs.hello.$refs.good);
  }
};
</script>
