<script setup lang="ts">
import * as ElIcons from '@element-plus/icons';

import { toLine } from '../../../utils';
import { useCopy } from '../../../hooks/useCopy/index.ts';

defineProps<{
  // 弹出框的标题
  title: string;
  // 控制弹出框的显示与隐藏
  visible: boolean;
}>();

const emits = defineEmits(['update:visible']);

// 点击按钮显示弹出框
const handleClick = (val: boolean) => {
  emits('update:visible', val);
};

// 点击图标
const clickItem = (item: string) => {
  let text = `<el-icon-${toLine(item)} />`;
  useCopy(text);
  handleClick(false);
};
</script>

<template>
  <el-button @click="handleClick(true)" type="primary">
    <slot></slot>
  </el-button>
  <div class="z-choose-icon-dialog-body-height">
    <el-dialog :title="title" :model-value="visible" @update:model-value="handleClick">
      <div class="container">
        <template v-for="item in Object.keys(ElIcons)" :key="item">
          <div class="item" @click="clickItem(item)">
            <component :is="`el-icon-${toLine(item)}`"></component>
            <div>{{ item }}</div>
          </div>
        </template>
      </div>
    </el-dialog>
  </div>
</template>

<style scoped lang="scss">
.container {
  display: flex;
  flex-wrap: wrap;
  align-items: center;

  .item {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 25%;
    margin-bottom: 20px;
    cursor: pointer;

    svg {
      width: 2em;
      height: 2em;
    }
  }
}
</style>
