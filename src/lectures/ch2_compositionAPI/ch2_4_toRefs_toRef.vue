<template>
  <div>
    <p>author: {{ author }}</p>
    <p>title: {{ title }}</p>
  </div>
</template>

<script>
import { reactive, toRefs } from 'vue';

export default {
  setup() {
    const book = reactive({
      author: 'Vue Team',
      year: '2020',
      title: 'Vue 3 Guide',
      description: '당신은 이 책을 지금 바로 읽습니다 ;)',
      price: '무료'
    });

    // const { author, title } = book; // 이따구로 구조 분해하면 반응성 잃음
    const { author, title } = toRefs(book);
    // const author = = toRefs(book, 'author'); // 따로 가져오고 싶을땐 이렇게

    return { author, title, book };
  }
};
</script>

<style lang="scss" scoped>

</style>