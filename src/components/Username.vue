<template>
  <div>
    <!-- 작동 방식 설명
      - :modelValue="firstname": modelValue를 firstname으로 재정의, 
          이때 이벤트명이 modelValue:update =>  firstname:update로 바뀜

      - @update:modelValue: modelValue 변경시 내부에 있는 함수 실행
        $emit('update:firstname', value): update:firstname 이벤트 호출

      - 만약 modelValue를 재정의하지 않으면 둘다 update:modelValue에 반응하기
          때문에 두 LabelInput의 값이 같이 바뀜, 그래서 각 라벨별로 event와 props를
          재정의하고 재정의된 이벤트명으로 호출함
    -->
    <LabelInput
      :modelValue="firstname"
      @update:modelValue="(value) => $emit('update:firstname', value)"
      label="first name">
    </LabelInput>
    <LabelInput
      :modelValue="lastname"
      @update:modelValue="(value) => $emit('update:lastname', value)"
      label="last name">
    </LabelInput>
  </div>
</template>

<script>
import LabelInput from './LabelInput.vue';

export default {
  props: ['firstname', 'lastname'],
  // 이벤트 선언
  emits: ['update:firstname', 'update:lastname'],
  components: {
    LabelInput,
  },
  setup() {
    return {};
  },
};
</script>

<style scoped>

</style>