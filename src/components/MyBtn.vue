<template>
  <div
    :class="{large}"
    :style="{backgroundColor: color}"
    class="btn">
    <!-- <slot>Button</slot> -->
    <!-- Fallback(대체) contents : <MyBtn></MyBtn>컴포넌트 사이에 다른 텍스트가 없으면 <slot></slot>태그 안에 있는 텍스트 출력됨-->
    <!-- 상속하는 App.vue에서 순서를 바꾸어도 컴포넌트 내에서 순서를 지정하였기 때문에, 순서를 보장함 -->
    <slot name="icon"></slot>
    <slot name="text"></slot>
  </div>
  <h1 v-bind="$attrs"></h1>
  <!-- <h1
    :class="$attrs.class"
    :style="$attrs.style"></h1> -->
  <!-- dblclick : 더블클릭 -->
  <h2 @dblclick="$emit('Dana', $event)">
    ABC
  </h2>

  <input
    type="text"
    v-model="msg" />
</template>

<script>

export default {
    emits: [
    'Dana',
    'changeMsg'
  ],
  data() {
    return {
      msg: ''
    }
  },
  watch: {
    msg() {
      this.$emit('changeMsg', this.msg)
    }
  },
  props: {
    color: {
      type: String,
      default: 'gray'
    }
  },
  large: {
    type: Boolean,
    default: false
  },
  text: {
    type: String,
    default: ''
  },
  // 최상위 요소에게도 상속하지 않겠다는 의미
  inheritAttrs: false,
  created() {
    console.log(this.$attrs)
  }
}
</script>

<style lang="scss" scoped>
  .btn {
    display: inline-block;
    margin: 4px;
    padding: 6px 12px;
    border-radius: 4px;
    background-color: gray;
    color: white;
    cursor: pointer;
    &.large {
      font-size: 20px;
      padding: 10px 20px;
    }
  }
</style>