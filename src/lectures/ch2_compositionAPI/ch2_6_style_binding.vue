<template>
  <!--동적 스타일 사용법-->
  <div :style="styleObject">
    afaslkfnbaslbnaslkgasgasgasgasgasgasgasgasg
  </div>
  <button @click="fontSize--">-</button>
  <button @click="fontSize++">+</button>
</template>

<script>
import { ref, computed } from 'vue';

export default {
  setup() {
    const fontSize = ref(13);
    const styleObject = computed(() => {
      return {
        color: 'red',
        fontSize: fontSize.value + 'px',
      };
    });
    return { fontSize, styleObject };
  },
};
</script>

<style scoped>

</style>