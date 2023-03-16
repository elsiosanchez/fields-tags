<template>
  <div class="demo-image">
    <el-image :src="url" :fit="fit" />
  </div>
</template>

<script lang="ts" setup>
import { computed } from 'vue';
const fits = ['fill', 'contain', 'cover', 'none', 'scale-down'];

const props = defineProps({
  src: {
    type: String,
    required: true,
    default:
      'https://upload.wikimedia.org/wikipedia/commons/b/b1/Adempiere-logo.png',
  },
  fit: {
    type: String,
    default: 'cover',
  },
});
const url = computed(() => {
  return props.src;
});
</script>

<style scoped>
.demo-image .block {
  padding: 30px 0;
  text-align: center;
  border-right: solid 1px var(--el-border-color);
  display: inline-block;
  width: 20%;
  box-sizing: border-box;
  vertical-align: top;
}
.demo-image .block:last-child {
  border-right: none;
}
.demo-image .demonstration {
  display: block;
  color: var(--el-text-color-secondary);
  font-size: 14px;
  margin-bottom: 20px;
}
</style>
