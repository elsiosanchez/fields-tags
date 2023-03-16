<template>
  <div>
    <slot name="header" />
    <br />
    <el-button> {{ text }} <slot name="content" /> </el-button>
    <br />
    <slot name="footer" />
  </div>
</template>

<script setup>
const props = defineProps({
  text: String,
  size: String,
  type: String,
  disabled: Boolean,
  plain: Boolean,
  round: Boolean,
  circle: Boolean,
  loading: Boolean,
});
</script>
