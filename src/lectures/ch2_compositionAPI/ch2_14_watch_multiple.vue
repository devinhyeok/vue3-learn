<template>
  <div></div>
</template>

<script>
import { ref, watch, reactive } from 'vue';

export default {
  setup() {
    const x = ref(0);
    const y = ref(0);

    const obj = reactive({
      count: 0,
    });

    // watch 응용: getter 함수를 감시하기
    // watch(
    //   () => x.value + y.value,
    //   (newValue, oldValue) => {
    //     console.log('sum: ', newValue);
    //   },
    // );

    // 여러 매개변수 감시하기
    watch([x, y], ([newX, newY]) => {
      console.log(newX, newY);
    });

    // 오브젝트 감시하기, 오브젝트는 old나 new나 같은 주소를 가르키기 때문에 값이 같음
    watch(obj, (newValue, oldValue) => {
      console.log('newValue: ', newValue);
      console.log('oldValue: ', oldValue);
    });

    // 오브젝트 값만 감시하기
    watch(
      () => obj.count,
      (newValue, oldValue) => {
        console.log('newValue: ', newValue);
      }
    );

    // deep option
    const person = reactive({
      name: '홍길동',
      age: 30,
      hobby: '운동',
      obj: {
        count: 0, // 객체안에 객체의 요소에도 반응!
      },
    });

    watch(person, (newValue) => {
      console.log('newValue: ', newValue);
    });

    // getter 함수 사용시 객체안에 값이 아닌 객체 자체가 바뀌었는지 검사함
    watch(
      () => person.obj,
      newValue => {
        console.log('onlyChangeObj: ', newValue);
      }
    );

    return { x, y, obj, person };
  },
};
</script>

<style scoped>

</style>