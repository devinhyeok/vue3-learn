<template>
  <div class="container py-4">
    <input ref="input" type="text" />
    <p>{{ input }}</p>
    <p v-if="input">
      <!--둘이 같은 -->
      {{ input.value }}, {{ $refs.input.value }}, {{ ($refs.input === input) }}
    </p>
    <hr />
    <!-- <ul>
      <li
        v-for="fruit in fruits"
        :key="fruit"
        :ref="el => itemRefs.push(el.textContent)">
        {{ fruit }}
      </li>
    </ul> -->
    <hr />
    <TemplateRefsChild ref="child"></TemplateRefsChild>
  </div>
</template>

<script>
import TemplateRefsChild from './TemplateRefsChild.vue';
import { onMounted, ref } from 'vue';

export default {
  components: {
    TemplateRefsChild,
  },
  setup() {
    const input = ref(null);
    console.log('setup: ', input.value);
    onMounted(() => {
      input.value.value = 'Hello World!';
      console.log('onMounted: ', input.value);

      itemRefs.value.forEach(item => console.log('item: ', item));
      console.log('child.message: ', child.value.message);
      child.value.sayHello();
    });

    const fruits = ref(['a', 'b', 'c']);
    const itemRefs = ref([]);

    const child = ref(null);
    return { input, fruits, itemRefs, child }
  }
}
</script>

<style scoped>

</style>