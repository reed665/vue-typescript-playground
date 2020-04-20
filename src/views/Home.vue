<template>
  <div class="home">
    <FullName ref="fullName" first-name="James" last-name="Bond" />
    <button @click="reverseFullName">Reverse full name</button>
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
  $refs!: {
    fullName: FullName;
  }

  reverseFullName(): void {
    this.$refs.fullName.reverse();
  }

}
</script>
