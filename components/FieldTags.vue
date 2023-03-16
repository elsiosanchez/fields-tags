<template>
  <el-tag :size="size" :type="type" :effect="effect" :round="round">
    {{ value }}
  </el-tag>
</template>

<script setup>
const props = defineProps({
  value: {
    type: String,
    required: true,
  },
  type: {
    type: String,
    required: false,
  },
  size: {
    type: String,
    default: 'default',
  },
  effect: {
    type: String,
    default: 'light',
  },
  round: {
    type: Boolean,
    default: false,
  },
});

const switchValue = ref(null);
switchValue.value = props.value;
</script>
