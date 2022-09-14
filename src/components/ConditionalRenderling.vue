<template>
  <button @click="handler">
    Click me!
  </button>
  <h1 v-if="isShow">
    Hello?!
  </h1>
  <h1 v-else-if="count > 3">
    Count > 3
  </h1>
  <h1 v-else>
    Good~
  </h1>

  <!-- v-if로 특정 요소들을 그룹으로 보이게 하거나 사라지게 하는 경우, template 태그 사용 / 단,최상위 template에는 사용 불가 -->
  <!-- v-show : display:none -->
  <template v-if="isShow">
    <h1>Title</h1>
    <p>Paragraph 1</p>
    <p v-show="isShow">
      Paragraph 2
    </p>
  </template>
</template>

<script>
export default {
  data() {
    return {
      isShow: false,
      count: 0
    }
  },
  methods: {
    handler() {
      this.isShow = !this.isShow
      this.count += 1
    }
  }
}
</script>