<template>
  <div class="home">
    <FullName ref="fullName" first-name="James" :last-name="lastName" />

    <div class="action" style="margin-top: 20px;">
      <button @click="reverseFullName">Reverse full name</button>
      <button @click="changeLastName">Change last name to Bond</button>
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
  lastName?: string = '';

  $refs!: {
    fullName: FullName;
  }

  created(): void {
    this.lastName = 'Jones';
  }

  changeLastName(): void {
    this.lastName = 'Bond';
  }

  reverseFullName(): void {
    this.$refs.fullName.reverse();
  }

}
</script>
