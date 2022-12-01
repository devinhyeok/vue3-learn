<template>
  <div>
    <!--v-model 없이 양반향 바인딩 구현-->
    <h2>input value</h2>
    <input type="text" :value="inputValue" @input="event => (inputValue = event.target.value)" />
    <div>{{ inputValue }}</div>
    <hr />

    <!--v-model: 양방향 바인딩-->
    <h2>input value</h2>
    <textarea v-model="textareaValue"></textarea>
    <div>{{ textareaValue }}</div>
    <hr />

    <!--양방향 바인딩 활용 예시 (체크박스)-->
    <h2>checkbox value</h2>
    <label for="checkbox">{{ checkboxValue }}</label>
    <input type="checkbox" id="checkbox" v-model="checkboxValue" />
    <hr />

    <!--양방향 바인딩 활용 예시 (라디오버튼)-->
    <h2>radio value</h2>
    <label><input type="radio" name="type" value="O" v-model="radioValue" />O형</label>
    <label><input type="radio" name="type" value="A" v-model="radioValue" />A형</label>
    <div>{{ radioValue }}</div>
    <hr />

    <!--양방향 바인딩 활용 예시 (드롭박스)-->
    <h2>select value</h2>
    <select v-model="selectValue">
      <option value="html">HTML 수업</option>
      <option value="css">CSS 수업</option>
      <option value="javascript">JavaScript 수업</option>
    </select>
    <div>{{ selectValue }}</div>
    <hr />

    <!--양방향 바인딩 활용 예시 (체크리스트)-->
    <h2>check list</h2>
    <label><input type="checkbox" value="html" v-model="checkListValue" />HTML</label>
    <label><input type="checkbox" value="css" v-model="checkListValue" />CSS</label>
    <label><input type="checkbox" value="javascript" v-model="checkListValue" />JavaScript</label>
    <div>{{ checkListValue }}</div>
    <hr />

    <!--lazy: 포커스를 잃었을때 바인딩되도록하는 modifiers-->
    <h2>lazy input value</h2>
    <textarea v-model.lazy="textareaValue1"></textarea>
    <div>{{ textareaValue1 }}</div>
    <hr />

    <!--number: 숫자로 자동형변환 해주는 modifiers-->
    <h2>number input value</h2>
    <textarea v-model.number="textareaValue2"></textarea>
    <div>{{ textareaValue2 }}</div>
    <div>{{ typeof textareaValue2 }}</div>
    <hr />

    <!--trim: 앞뒤 공백을 제거해주는 modifiers-->
    <h2>trim input value</h2>
    <textarea v-model.trim="textareaValue3"></textarea>
    <div>{{ textareaValue3 }}</div>
    <div>{{ typeof textareaValue3 }}</div>
    <hr />
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  setup() {
    const inputValue = ref('');
    const textareaValue = ref('');
    const checkboxValue = ref(true);
    const radioValue = ref('O');
    const selectValue = ref('html');
    const checkListValue = ref([]);
    const textareaValue1 = ref('');
    const textareaValue2 = ref('');
    const textareaValue3 = ref('');
    return {
      inputValue,
      textareaValue,
      checkboxValue,
      radioValue,
      selectValue,
      checkListValue,
      textareaValue1,
      textareaValue2,
      textareaValue3
    };
  },
};
</script>

<style scoped>

</style>