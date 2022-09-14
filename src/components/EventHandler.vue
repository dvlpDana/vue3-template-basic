<template>
  <button @click="handler('hi', $event)">
    Click 1
  </button>
  <button @click="handler('what', $event)">
    Click 2
  </button>
  <!-- 하나의 요소에서 발생할 이벤트가 여러개일 경우, 쉼표로 구분하되 메소드를 호출하겠다는 소괄호 반드시 입력할 것, 소괄호 입력하지 않으면 메소드 실행되지 않음-->
  <button @click="handlerA(), handlerB()">
    Click Me
  </button>
  <a
    href="http://naver.com"
    target="blank"
    @click.once="handlerC">NAVER</a>
  <!-- @click.prevent : 기존의 이벤트 막고자 할 때 -->
  <input
    type="text"
    @keydown.enter="handlerD" />
  <!-- @keydown.ctrl.shif.a 와 같이 chaining이 가능함 -->

  <h1>{{ msg }}</h1>
  <input
    type="text"
    v-model="msg" />
  
  <h1>{{ checked }}</h1>
  <input
    type="checkbox"
    v-model="checked" />
  <!--한글로 작성 시 :value="msg"
    @input="msg = $event.target.value"  -->
  <!-- 양방향 데이터 바인딩 : 한글로 작성할 때는 한박자 느리게 됨-->
  <!-- @change : 더이상 input요소에 포커스가 되지 않는 상황을 만들게 되면 반응성이 나타남, 입력을 하는 동안에는 값이 갱신되지 않고 입력이 완료되면 값이 갱신됨 
    value="msg"
    @change = "msg = $event.target.value"
    위의 두 코드를 아래의 코드로 변환할 수 있음
    v-model.lazy="msg"
    문자열이 아닌 특정 타입을 설정하려면
    v-model.number="msg"
    띄어쓰기 제거하려면
    v-model.trim="msg"
    -->
</template>

<script>
export default {
  data() {
    return {
      msg: "Hello world!",
      checked: false
    };
  },
  methods: {
    handler(msg, event) {
      console.log(msg);
      console.log(event);
      console.log(event.target.textContent);
    },
    handlerA() {
      console.log("A");
    },
    handlerB() {
      console.log("B");
    },
    handlerC() {
      console.log("ABC!");
    },
    handlerD(event) {
      // if (event.key === "Enter") {
      //   console.log(event);
      // }
      console.log(event);
    }
    // handlerE(event) {
    //   console.log(event.target.value);
    //   this.msg = event.target.value;
    // }
  }
};
</script>
