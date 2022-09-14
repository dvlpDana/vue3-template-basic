<template>
  <!-- computed -->
  <Fruits />

  <button @click="add">
    ADD
  </button>
  <!-- computed cashing : 한번 연산 후, 다시 안함 -->
  <h1>{{ reversedMessage }}</h1>
  <h1>{{ reversedMessage }}</h1>
  <h1>{{ reversedMessage }}</h1>
  <h1>{{ reversedMessage }}</h1>
  <!-- methods : 반복하여 연산 후, 출력함 / 부하 가능성 높음 -->
  <h1>{{ reverseMessage() }}</h1>
  <h1>{{ reverseMessage() }}</h1>
  <h1>{{ reverseMessage() }}</h1>
  <h1>{{ reverseMessage() }}</h1>

  <!-- watch -->
  <h1 @click="changeMessage">
    {{ msg2 }}
  </h1>
  <h1>{{ reversedMessage }}</h1>
  
  <ListRenderlingVue />

  <!-- components -->
  <MyBtn
    class="Dana"
    style="color: red;"
    title="Hello World">
    <span style="color: red;">Banana</span>
  </MyBtn>
  <!-- 컴포넌트에 연결하는 이벤트의 이름은 실제로 사용하는 이벤트의 이름이 아니어도 상관없음 -->
  <MyBtn
    large
    @Dana="log"
    @change-msg="logMsg">
    Apple
  </MyBtn>
  <MyBtn color="royalblue">
    Cherry
  </MyBtn>
  <MyBtn :color="color">
    Melon
  </MyBtn>
  <MyBtn>
    <template #icon>
      <span>Banana</span>
    </template>
    <template #text>
      <span>(B)</span>
    </template>
  </MyBtn>
</template>

<script>
import Fruits from "~/components/Fruits";
import ListRenderlingVue from "./components/ListRenderling.vue";

// component
import MyBtn from "~/components/MyBtn";

export default {
  components: {
    Fruits,
    ListRenderlingVue,
    MyBtn
  },
  data() {
    return {
      //Getter : 값을 읽어들이는 용도, Setter : 값을 지정하는 용도
      msg: "Hello computed",
      msg2: "Hello?",
      color: "#000"
    };
  },
  // 계산된 데이터는 캐싱이라는 기능이 있음, 한번 연산을 해놓은 값이 있으면 반복적으로 출력할 때 값을 다시 연산하지 않음
  // Getter : 읽기 전용
  computed: {
    reversedMessage: {
      get() {
        return this.msg2.split("").reverse().join("");
      },
      // set(newValue) {
      //   this.msg = newValue;
      //   console.log(newValue);
      // }
    }
  },
  // 특정한 데이터가 변경되는 것을 감시해서 추가적인 로직을 만들어낼 때 watch 사용
  // newValue 매개변수는 원하는 이름으로 수정하여 사용가능함
  watch: {
    // msg2: function(){}
    msg2(newValue) {
      console.log('msg2', newValue)
    },
    reversedMessage(newValue) {
      console.log('reversedMessage: ', newValue)
    }
  },
  methods: {
    reverseMessage() {
      return this.msg.split("").reverse().join("");
    },
    add() {
      this.reversedMessage += "!?";
    },
    changeMessage() {
      this.msg2 = 'Good!'
    },
    log() {
      console.log('Click!!')
      console.log(event)
    },
    logMsg(msg) {
      console.log(msg)
    }
  }
};
</script>
