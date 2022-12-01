<template>
  <div>
    <!--조건부 렌더링-->
    <h2 v-if="visible">True</h2>
    <h2 v-else>False</h2>
    <button @click="visible = !visible">toggle</button>
    <hr />
    <!--조건부 렌더링 2-->
    <h2 v-if="type === 'A'">A</h2>
    <h2 v-else-if="type === 'B'">B</h2>
    <h2 v-else-if="type === 'C'">C</h2>
    <h2 v-else>!A & !B & !C</h2>
    <button @click="type = 'A'">A</button>
    <button @click="type = 'B'">B</button>
    <button @click="type = 'C'">C</button>
    <button @click="type = 'D'">D</button>
    <hr />
    <!--조건부 렌더링 3-->
    <template v-if="visible">
      <h1>Title</h1>
      <p>Paragraph 1</p>
      <p>Paragraph 2</p>
    </template>
    <hr />
    <h1 v-show="ok">Title</h1>
    <button @click="ok = !ok">toggle</button>
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  setup() {
    const visible = ref(true);
    const type = ref('A');
    const ok = ref(true);
    return { visible, type, ok };
  },
};
</script>

<style scoped>

</style>