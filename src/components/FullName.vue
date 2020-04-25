<template>
  <div class="full-name">
    <div class="first-name">{{ fullName }}</div>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Prop } from 'vue-property-decorator';

const reverseString = (str: string): string => {
  return str.split('').reverse().join('');
}

@Component
export default class FullName extends Vue {
  reversed = false;

  @Prop({ type: String, required: true })
  private readonly firstName!: string;

  @Prop({ type: String, default: '' })
  private readonly lastName?: string;

  get fullName(): string {
    let name = this.firstName;
    if (this.lastName) {
      name += ` ${this.lastName}`;
    }
    return (this.reversed) ? reverseString(name) : name;
  }

  public reverse(): void {
    this.reversed = !this.reversed;
  }

}
</script>