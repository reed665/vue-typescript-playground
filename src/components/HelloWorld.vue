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
