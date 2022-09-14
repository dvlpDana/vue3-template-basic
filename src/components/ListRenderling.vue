<template>
  <!-- 객체 구조분해 -->
  <div>
    <button @click="handler">
      Click me!
    </button>
    <ul>
      <li
        v-for="{id, name} in newFruits"
        :key="id">
        {{ name }}-{{ id }}
      </li>
    </ul>
  </div>
</template>

<script>
import shortid from "shortid";
export default {
  data() {
    return {
      fruits: ["Apple", "Banana", "Cherry"]
      // newFruits: [
      //   { id: 0, name: 'Apple' },
      //   { id: 1, name: 'Banana' },
      //   { id: 2, name: 'Cherry'}
      // ]
    };
  },
  computed: {
    // 실제로 사용하는 대부분의 데이터들은 배열 데이터 안에 객체 데이터가 들어있고, 객체 데이터 내부에는 복잡한 속성들로 데이터가 구분되어 있음
    // 반복되는 데이터를 구분할 수 있는 고유한 속성들을 활용하여 출력하여야 최적화시킬 수 있음
    newFruits() {
      return this.fruits.map(fruit => ({
        id: shortid.generate(),
        name: fruit
      }));
    }
  },
  methods: {
    handler() {
      this.fruits.push('Orange')
    }
  }
};
</script>

<style lang="scss" scoped>
  div {
    background-color: lightblue;
    padding: 3rem;
    ul{
      padding : 2rem;
      background-color: white;
    }
  }
</style>