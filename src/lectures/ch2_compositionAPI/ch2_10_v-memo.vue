<template>
  <div>
    <div>
      <p>subscribers: {{ subscribers }}</p>
      <p>views: {{ views }}</p>
      <p>likes: {{ likes }}</p>
    </div>
  </div>
  <hr />
  <!--v-meom: v-once와 같지만 특정 데이터에만 반응하도록 지정해줄 수 있음, 최적화용-->
  <div>
    <div v-memo="[subscribers]">
      <p>subscribers: {{ subscribers }}</p>
      <p>views: {{ views }}</p>
      <p>likes: {{ likes }}</p>
    </div>
  </div>
  <button @click="subscribers++">Subs++</button>
  <button @click="views++">Views++</button>
  <button @click="likes++">Likes++</button>
</template>

<script>
import { ref } from 'vue';

export default {
  setup() {
    const subscribers = ref(4000);
    const views = ref(400);
    const likes = ref(20);
    return { subscribers, views, likes };
  },
};
</script>

<style scoped>

</style>