<template>
  <div class="full-name">
    <p>{{ fullName }}</p>

    <div class="actions">
      <button @click="$emit('reset-name')">Reset name</button>
      <button @click="switchNames">Switch first and last names</button>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Prop, Watch, Emit } from 'vue-property-decorator';
import { Person } from '@/helpers';

const reverseString = (str: string): string => {
  return str.split('').reverse().join('');
}

@Component
export default class FullName extends Vue {
  private reversed = false;

  @Prop({ type: String, required: true })
  private readonly firstName!: string;

  @Prop({ type: String, default: '' })
  private readonly lastName?: string;

  private get fullName(): string {
    let name = this.firstName;
    if (this.lastName) {
      name += ` ${this.lastName}`;
    }
    return (this.reversed) ? reverseString(name) : name;
  }

  @Watch('lastName', { immediate: true })
  handleLastNameChange(newVal: string, oldVal: string) {
    console.log(`last name has been changed from "${oldVal}" to "${newVal}"`)
  }

  reverse(): void {
    this.reversed = !this.reversed;
  }

  @Emit('switch-names')
  switchNames() {
    const person: Person = {
      firstName: this.lastName || '',
      lastName: this.firstName,
    }
    return person;
  }

}
</script>

<style lang="scss" scoped>
.full-name {
  padding: 10px;
  background: lightgoldenrodyellow;
}
</style>