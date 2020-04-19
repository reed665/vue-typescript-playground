<template>
  <div class="FooBar">
    <h3>
      Hello from FooBar component!!
    </h3>

    <p>
      {{ foo }}
    </p>

    <p>{{ theNumber }}</p>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';

@Component
export default class FooBar extends Vue {
  @Prop({ type: String, required: false, default: 'bar' })
  private foo: string | undefined;

  private theNumber?: number;

  created() {
    this.theNumber = 42;
  }

}
</script>
