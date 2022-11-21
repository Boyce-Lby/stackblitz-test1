<script setup lang="ts">
import { ref, reactive, onMounted, watch } from 'vue';
const props = defineProps<{
  list: any[];
}>();

const waterList = reactive<any[]>([]);
const heightList: number[] = [];
const init = () => {
  const width = 130;
  const x = document.body.clientWidth;
  const column = Math.floor(x / width);
  for (let i = 0; i < props.list.length; i++) {
    console.log(props.list[i]);
    if (i <= column) {
      props.list[i].top = 20;
      props.list[i].left = width * i;
      // waterList.push(props.list[i]);
      heightList.push(props.list[i].height + 20);
    } else {
      let curent = heightList[0];
      let index = 0;
      heightList.forEach((h, a) => {
        if (curent >= h) {
          curent = h;
          index = a;
        }
      });
      props.list[i].top = curent + 20;
      props.list[i].left = index * width;
      heightList[index] = props.list[i].height + heightList[index] + 20;
    }
    waterList.push(props.list[i]);
  }
};

onMounted(() => {
  init();
  console.log(waterList);
});
import gsap from 'gsap';
const myNum = reactive({
  current: 0,
  tweenedNumber: 0,
});
watch(
  () => myNum.current,
  (newVal, oldVal) => {
    gsap.to(myNum, {
      duration: 1,
      tweenedNumber: newVal,
    });
  }
);
</script>

<template>
  <div>
    <input v-model="myNum.current" step="20" type="number" />
    <div>{{ myNum.tweenedNumber.toFixed(0) }}</div>
  </div>
  <div class="wraps">
    <div
      :style="{
        height: item.height + 'px',
        background: item.backgroud,
        left: item.left + 'px',
        top: item.top + 'px',
      }"
      v-for="item in waterList"
      class="item"
    ></div>
  </div>
</template>

<style scoped>
.wraps {
  position: relative;
}
.item {
  position: absolute;
  width: 120px;
}
</style>
