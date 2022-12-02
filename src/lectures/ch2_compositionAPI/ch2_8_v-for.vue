<template>
  <div>
    <ul>
      <!--:key 속성은 정렬시 순서에 힌트를 줍니다-->
      <template v-for="(item, index) in items" :key="item.id">
        <li>{ index: {{ index }}, id: {{ item.id }}, message: {{ item.message }} }</li>
      </template>
    </ul>
    <hr />
    <ul>
      <!--index와 key값은 다릅니다-->
      <template v-for="(item, index) in evenItems" :key="item.id">
        <li>{ index: {{ index }}, id: {{ item.id }}, message: {{ item.message }} }</li>
      </template>
    </ul>
    <hr />
    <ul>
      <!--객체의 속성을 반복하는법-->
      <li v-for="(value, key, index) in myObject" :key="key">
        { index: {{ index }}, key: {{ key }}, value: {{ value }} }
      </li>
    </ul>
  </div>
</template>

<script>
import { reactive, computed } from 'vue';

export default {
  setup() {
    const items = reactive([
      { id: 1, message: 'Java' },
      { id: 2, message: 'HTML' },
      { id: 3, message: 'CSS' },
      { id: 4, message: 'JavaScript' },
    ]);

    const evenItems = computed(() =>
      items.filter(item => item.id % 2 === 0)
    );

    const myObject = reactive({
      title: '제목',
      author: '홍길동',
      publishedAt: '2016-01-01',
    });
    return { items, evenItems, myObject };
  },
};
</script>

<style scoped>

</style>