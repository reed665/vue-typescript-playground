<template>
  <div class="hello">
    <h1>{{ msg }}</h1>

    <FooBar foo="foobaarrrr" />
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
import FooBar from './FooBar.vue';

@Component({
  components: {
    FooBar,
  }
})
export default class HelloWorld extends Vue {
  @Prop()
  private msg!: string;
  
}
</script>

<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
