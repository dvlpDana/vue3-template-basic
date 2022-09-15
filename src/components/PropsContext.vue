<template>
  <PCBtn
    class="pcbtn"
    style="color: red;"
    color="#ff0000"
    @hello="log">
    Apple
  </PCBtn>
</template>
<script>
import PCBtn from '~/components/PCBtn'

export default {
  components: {
    PCBtn
  },
  methods: {
    log() {
      console.log('Hello world!')
    }
  }
}
</script>