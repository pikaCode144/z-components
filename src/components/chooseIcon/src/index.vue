<script setup lang="ts">
const props = defineProps<{
  // 弹出框的标题
  title: string;
  // 控制弹出框的显示与隐藏
  visible: boolean;
}>();
const emits = defineEmits(['update:visible']);
const handleClick = () => {
  emits('update:visible', !props.visible);
};
</script>

<template>
  <el-button @click="handleClick" type="primary">
    <slot></slot>
  </el-button>
  <el-dialog :title="title" :model-value="visible" @update:model-value="handleClick">
    111
  </el-dialog>
</template>

<style scoped></style>
