<template>
  <!--그냥 쓰면 span클릭시 { span -> p -> div } 순으로 이벤트 전파됨-->
  <div id="modifiers">
    <div @click="clickDiv">
      DIV 영역
      <p @click="clickP">
        P 영역
        <!--stop: 이벤트 전파를 막는 modifire-->
        <span @click.stop="clickSpan">
          SPAN 영역
        </span>
        <!--stop, prevent 동시 사용-->
        <a href="https://naver.com" @click.prevent.stop="clickA">바로가기</a>
      </p>
    </div>
    <!--prevent: 기본 기능을 막는 modifire-->
    <a href="https://naver.com" @click.prevent="clickA">바로가기</a>
  </div>

  <hr />

  <!--전파 경로: capture { div -> p -> span } => bubble { span -> p -> div }-->
  <div id="modifiers">
    <!--capture를 붙히면 capture 단계에서 이벤트 발생 -->
    <div @click.capture="clickDiv">
      DIV 영역
      <!--타겟이 나 자신일 때만 동작, 이벤트 전파받지 않음-->
      <p @click.self="clickP">
        P 영역
        <span @click="clickSpan">
          SPAN 영역
        </span>
      </p>
    </div>
  </div>

  <hr />

  <!--once: 한번만 발생하는 버튼-->
  <button @click.once="clickA">바로가기</button>
</template>

<script>
export default {
  setup() {
    const clickDiv = () => {
      console.log('clickDiv');
    }
    const clickP = () => {
      console.log('clickP');
    }
    const clickSpan = () => {
      console.log('clickSpan');
    }
    const clickA = () => {
      alert("바로가기");
    }
    return {
      clickDiv,
      clickP,
      clickSpan,
      clickA,
    };
  },
};
</script>

<style scoped>
#modifiers div,
#modifiers p,
#modifiers span {
  padding: 40px;
}

#modifiers div {
  background-color: #ccc;
}

#modifiers p {
  background-color: #999;
}

#modifiers span {
  background-color: #666;
  display: block;
}
</style>