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
import { defineComponent, ref, computed } from '@vue/composition-api';
import { Person } from '@/helpers';

const reverseString = (str: string): string => {
  return str.split('').reverse().join('');
}

export interface FullNamePublicMethods {
  reverse: () => void;
}

export default defineComponent({
  props: {
    firstName: {
      type: String,
      required: true
    },
    lastName: {
      type: String,
      default: ''
    }
  },

  setup(props, context) {
    const reversed = ref(false)

    const reverse = (): void => {
      reversed.value = !reversed.value;
    }

    const fullName = computed(() => {
      let name = props.firstName;
      if (props.lastName) {
        name += ` ${props.lastName}`;
      }
      return reversed.value ? reverseString(name) : name;
    })

    const switchNames = () => {
      const person: Person = {
        firstName: props.lastName,
        lastName: props.firstName,
      }
      context.emit('switch-names', person);
    }

    return {
      fullName,
      reverse,
      switchNames,
    }
  }

})
</script>

<style lang="scss" scoped>
.full-name {
  padding: 10px;
  background: lightgoldenrodyellow;
}
</style>