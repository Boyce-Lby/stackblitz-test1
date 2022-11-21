<script setup lang="ts">
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import HelloWorld from './components/HelloWorld.vue';
import { ref, reactive } from 'vue';
const list = [
  {
    height: 160,
    backgroud: 'red',
  },
  {
    height: 123,
    backgroud: 'blue',
  },
  {
    height: 154,
    backgroud: 'green',
  },
  {
    height: 122,
    backgroud: 'blue',
  },
  {
    height: 199,
    backgroud: 'blue',
  },
  {
    height: 200,
    backgroud: 'green',
  },
  {
    height: 110,
    backgroud: 'black',
  },
  {
    height: 186,
    backgroud: 'blue',
  },
  {
    height: 156,
    backgroud: 'red',
  },
  {
    height: 143,
    backgroud: 'black',
  },
  {
    height: 123,
    backgroud: 'green',
  },
  {
    height: 132,
    backgroud: 'black',
  },
  {
    height: 155,
    backgroud: 'blue',
  },
  {
    height: 177,
    backgroud: 'red',
  },
  {
    height: 186,
    backgroud: 'black',
  },
  {
    height: 154,
    backgroud: 'green',
  },
];
</script>

<template>
  <div>
    <HelloWorld :list="list" />
  </div>
</template>

<style scoped></style>
