<script setup lang="ts">
import { ref } from 'vue';
import zChooseIcon from '../../components/chooseIcon/src/index.vue';

const visible = ref(false);
</script>

<template>
  <div class="app">
    <z-choose-icon title="选择图标" v-model:visible="visible"> 选择图标 </z-choose-icon>
  </div>
</template>

<style scoped></style>
