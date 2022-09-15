<template>
  <h1 @click="increase">
    {{ count }} / {{ doubleCount }}
  </h1>
  <h1 @click="changeMessage">
    {{ message }} / {{ reversedMessage }}
  </h1>
</template>

<script>
import { ref, computed, watch, onMounted } from "vue";

export default {
  setup() {
    const message = ref("Hello World!");
    function changeMessage() {
      message.value = "Good?!";
    }
    const reversedMessage = computed(() => {
      return message.value.split("").reverse().join("");
    });
    // value를 사용하는 것이 아니라 ref라는 함수를 통해 반응성을 가지는 message를 첫번째 파라미터로 입력
    // 해당되는 데이터의 변경이 감지되었을 때, 그 내용을 그대로 콜백으로 만들어주기
    watch(message, (newValue) => {
      console.log(newValue);
    });
    // onCreated라는 메소드는 없음. setup메소드 내부에서 어디서든지 실행하면 됨, setup이라는 메소든는 컴포넌트가 생성된 직후에 동작하기 때문임
    onMounted(() => {
      console.log(count.value);
    });



    const count = ref(0);
    const doubleCount = computed(() => count.value * 2);
    function increase() {
      count.value += 1;
    }

    return {
      // 속성과 데이터의 값이 같다면, 데이터를 생략해주어도 됨. 원래는 count=count
      message,
      changeMessage,
      reversedMessage,
      count,
      doubleCount,
      increase
    };
  }
};
</script>
