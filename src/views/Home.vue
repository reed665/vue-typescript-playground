<template>
  <div class="home">
    <FullName ref="fullName" first-name="James" :last-name="lastName" />

    <div class="action" style="margin-top: 20px;">
      <button @click="reverseFullName">Reverse full name</button>
      <button @click="changeLastName">Change last name</button>
    </div>

  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import FullName from '@/components/FullName.vue';

@Component({
  components: {
    FullName,
  }
})
export default class Home extends Vue {
  lastName?: string = 'Jones';

  $refs!: {
    fullName: FullName;
  }

  changeLastName(): void {
    this.lastName = (this.lastName === 'Jones') ? 'Bond' : 'Jones';
  }

  reverseFullName(): void {
    this.$refs.fullName.reverse();
  }

}
</script>
