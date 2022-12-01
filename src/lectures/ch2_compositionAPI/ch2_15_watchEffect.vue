<template>
  <div>
    <form @submit.prevent>
      <input v-model.lazy="title" type="text" placeholder="Title" />
      <hr />
      <textarea v-model.lazy="contents" placeholder="Contents"></textarea>
      <hr />
      <button @click="save(title, contents)">심리적 안정을 주는 저장 버튼</button>
    </form>
  </div>
</template>

<script>
import { ref, watchEffect } from 'vue';

export default {
  setup() {
    const title = ref('');
    const contents = ref('');

    const save = (title, contents) => {
      console.log(`save: {title: ${title}, contents: ${contents}}`);
    }

    // watch랑 달리 값을 지정하지 않아도 내부 변수가 변경되면 자동으로 호출한다
    // watch는 시작시 반드시 즉시실행을 한다.
    watchEffect(() => {
      save(title.value, contents.value);
    });
    return { title, contents, save };
  },
};
</script>

<style scoped>

</style>