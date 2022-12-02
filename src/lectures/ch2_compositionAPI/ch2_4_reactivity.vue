<template>
  <div>
    <button v-on:click="increment">Click {{ state.count }}</button>
    <button v-on:click="increment">Deep Click {{ state.deep.count }}</button>
  </div>
</template>

<script>
import { reactive } from 'vue';

export default {
  setup() {
    // 반응형 객체 선언
    const state = reactive({
      count: 0,
      deep: {
        count: 0,
      },
    });
    const increment = () => {
      state.count++;
      state.deep.count++;
    };
    return {
      state,
      increment,
    };
  },
};
</script>

<style lang="scss" scoped>

</style>