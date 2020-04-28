<template>
  <div class="home">
    <FullName
      ref="fullNameRef"
      :first-name="firstName"
      :last-name="lastName"
      @reset-name="handleResetName"
      @switch-names="handleSwitchNames"
    />

    <div class="action" style="margin-top: 20px;">
      <button @click="reverseFullName">Reverse full name</button>
      <button @click="changeLastName">Change last name</button>
    </div>

  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from '@vue/composition-api';
import FullName, { FullNamePublicMethods } from '@/components/FullName.vue';
import { Person } from '@/helpers';

export default defineComponent({
  components: {
    FullName,
  },

  setup() {
    const firstName = ref('')
    const lastName = ref('')

    const fullNameRef = ref<FullNamePublicMethods>(null)

    const setDefaultName = () => {
      firstName.value = 'James';
      lastName.value = 'Bond';
    }

    setDefaultName()

    const handleResetName = () => {
      setDefaultName()
    }

    const handleSwitchNames = (person: Person) => {
      firstName.value = person.firstName;
      lastName.value = person.lastName;
    }

    const reverseFullName = () => {
      fullNameRef.value?.reverse()
    }

    const changeLastName = () => {
      lastName.value = (lastName.value === 'Bond') ? 'Jones' : 'Bond';
    }

    return {
      firstName,
      lastName,
      fullNameRef,
      reverseFullName,
      changeLastName,
      handleResetName,
      handleSwitchNames,
    }
  }

})

</script>
