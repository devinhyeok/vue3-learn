<template>
    <div>
        <p>강의가 존재 합니까?:</p>
        <!-- <span>{{ teacher.lectures.length > 0 ? 'Yes' : 'No' }}</span> -->
        <p>{{ hasLecture }}</p> <!--함수로 사용 가능-->
        <p>{{ hasLecture }}</p> <!--캐시로 결과값을 보관해서 한번만 출력됨-->
        <p>{{ existLecture() }}</p>
        <p>{{ existLecture() }}</p>
        <button v-on:click="counter++">Counter: {{ counter }}</button>
        <p>{{ fullName }}</p>
    </div>
</template>

<script>
import { computed, reactive, ref } from 'vue';

export default {
    setup() {
        const teacher = reactive({
            name: '짐코딩',
            lectures: [
                'HTML/CSS',
                'JavaScript',
                'Vue3'
            ],
        });

        // computed를 통해 반응형 함수 선언
        const hasLecture = computed(() => {
            console.log('computed');
            return teacher.lectures.length > 0 ? 'Yes' : 'No';
        });

        // 이렇게 사용가능하지만 computed가 더 연산 비용이 쌈
        const existLecture = () => {
            console.log('method');
            return teacher.lectures.length > 0 ? 'Yes' : 'No';
        }
        const counter = ref(0);

        // computed에 getter setter 지정할 수 있음
        const firstName = ref('lee');
        const lastName = ref('inhyeok');
        const fullName = computed({
            get() {
                return firstName.value + ' ' + lastName.value;
            },
            set(value) {
                [firstName.value, lastName.value] = value.split(' ');
            },
        });
        fullName.value = "홍 길동"

        return {
            teacher,
            hasLecture,
            existLecture,
            counter,
            fullName,
        };
    },
};
</script>

<style lang="scss" scoped>

</style>