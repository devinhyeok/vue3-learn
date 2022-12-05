<template>
  <div class="container py-4">
    <button
      class="btn btn-primary me-2"
      @click="changeCurrentComp(DynamicApple)">
      apple
    </button>
    <button
      class="btn btn-danger"
      @click="changeCurrentComp(DynamicBanana)">
      banana
    </button>
    <hr />
    <component :is="currentComp" />
    <p>{{ obj1 }}</p>
    <p>{{ obj2 }}</p>
  </div>
</template>

<script setup>
import { ref, shallowRef } from 'vue';
import DynamicApple from './DynamicApple.vue';
import DynamicBanana from './DynamicBanana.vue';

// 컴포넌트 전환시 shallowRef 함수를 사용할 것 (성능)
const currentComp = shallowRef(DynamicApple);
const changeCurrentComp = (comp) => (currentComp.value = comp);

const obj1 = ref({ name: '1' });
const obj2 = shallowRef({ name: '2' }); // 포인터가 바뀌었을때만 반응
</script>

<style scoped>

</style>
