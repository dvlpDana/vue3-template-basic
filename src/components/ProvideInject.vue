<template>
  <button @click="message = 'Good?'"></button>
  <h1>App: {{ message }}</h1>
  <Parent />
</template>

<script>
import Parent from "~/components/Parent";
import { computed } from "vue";

export default {
  components: {
    Parent
  },
  data() {
    return {
      message: "Hello world!"
    };
  },
  // provide 사용 시에는 반응성을 사용할 수 없음, 간단히 데이터를 전달해서 출력하는 용도로 사용하거나 반응성을 유지하도록 추가적으로 코드 작성해야함
  provide() {
    return {
      msg: computed(() => this.message)
    };
  }
};
</script>
