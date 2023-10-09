<script setup lang="ts">
const props = defineProps<{
  collapse: boolean;
}>();
const emits = defineEmits(['update:collapse']);
const toggle = () => {
  emits('update:collapse', !props.collapse);
};
</script>

<template>
  <span @click="toggle" class="header">
    <el-icon-expand v-if="collapse" />
    <el-icon-fold v-else />
  </span>
</template>

<style scoped>
.header {
  display: flex;
  align-items: center;
  height: 60px;
  padding: 0 20px;
}
</style>
