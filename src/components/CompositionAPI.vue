<template>
  <h1 @click="increase">
    {{ count }} / {{ doubleCount }}
  </h1>
  <h1 @click="changeMessage">
    {{ message }} / {{ reversedMessage }}
  </h1>
</template>

<script>
export default {
  data() {
    return {
      message: 'Hello world!',
      count: 0
    }
  },
  computed: {
    doubleCount() {
      return this.count * 2
    },
    reversedMessage() {
      return this.message.split('').reverse().join('')
    }
  },
  // message에서 데이터가 변경되면 watch의 옵션을 통해서 message라는 메소드가 실행됨
  watch: {
    message(newValue) {
      console.log(newValue)
    }
  },
  //created: 컴포넌트가 생성된 직후에 실행
  created() {
    console.log(this.message)
  },
  //mounted : html과 컴포넌트가 연결된 직후에 실행
  mounted() {
    console.log(this.count)
  },
  methods: {
    increase() {
      this.count += 1
    },
    changeMessage() {
      this.message = 'Good?!'
    }
  }
}
</script>