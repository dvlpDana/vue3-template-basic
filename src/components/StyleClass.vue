<template>
  <h1
    :class="{ active: isActive }"
    @click="activate">
    Hello?!({{ isActive }})
  </h1>
  <!-- 여러 개의 객체 데이터를 연결할 때는, 배열 구문 안에 삽입 -->
  <h2
    :style="[fontStyle, backgroundStyle]"
    @click="changeStyle">
    Hello?!
  </h2>
</template>

<script>
export default {
  data() {
    return {
      isActive: false,
      fontStyle: {
        color: "orange",
        fontSize: "30px"
      },
      backgroundStyle: {
        backgroundColor: 'black'
      }
    };
  },
  methods: {
    activate() {
      this.isActive = true;
    },
    changeStyle() {
      this.fontStyle.color = "red";
      this.fontStyle.fontSize = "50px";
    }
  }
};
</script>

<style scoped>
.active {
  color: red;
  font-weight: bold;
}
</style>
