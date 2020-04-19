<template>
  <div class="home">
    <HelloWorld msg="Hello from Vue.js + Typescript App" />
  </div>
</template>

<script>
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'Home',
  components: {
    HelloWorld
  }
}
</script>
