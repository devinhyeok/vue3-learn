<template>
  <label class="form-label" id="child-id">
    <!--props에 등록된 속성은 template에서 바로 사용가능-->
    {{ label }}
  </label>
  <input v-model="value" v-bind="$attrs" type="text" class="form-control" />
</template>

<script>
import { computed } from '@vue/reactivity';

export default {
  // props: 컴포넌트에 등록할 수 있는 사용자 정의 속성
  props: ['modelValue', 'label'],
  emits: ['update:modelValue'],
  // setup() 함수에서 props 객체를 받아 사용 가능
  setup(props, { emit }) {
    // props.label = 'changed label' // 상위컴포넌트에 반영되지 않음
    // 상위 컴포넌트에 반영되고 싶으면 computed를 사용할 것
    const value = computed({
      get() {
        return props.modelValue;
      },
      set(value) {
        // emit을 이용해 부모 컴포넌트가 스스로 변경하도록 유도
        emit('update:modelValue', value);
      },
    })
    return { value };
  },
};
</script>

<style scoped>

</style>