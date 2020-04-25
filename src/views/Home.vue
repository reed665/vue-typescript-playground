<template>
  <div class="home">
    <FullName
      ref="fullName"
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
import { Component, Vue } from 'vue-property-decorator';
import FullName from '@/components/FullName.vue';
import { Person } from '@/helpers';

@Component({
  components: {
    FullName,
  }
})
export default class Home extends Vue {
  firstName = '';
  lastName = '';

  $refs!: {
    fullName: FullName;
  }

  created() {
    this.setDefaultName();
  }

  changeLastName(): void {
    this.lastName = (this.lastName === 'Jones') ? 'Bond' : 'Jones';
  }

  reverseFullName(): void {
    this.$refs.fullName.reverse();
  }

  private setDefaultName() {
    this.firstName = 'James';
    this.lastName = 'Jones';
  }

  handleResetName() {
    this.setDefaultName();
  }

  handleSwitchNames(person: Person) {
    this.firstName = person.firstName;
    this.lastName = person.lastName || '';
  }

}
</script>
