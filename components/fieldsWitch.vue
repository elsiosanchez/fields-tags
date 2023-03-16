<template>
  <div>
    <!-- <slot name="header" /> -->
    <!-- <br /> -->
    <el-switch
      v-model="switchValue"
      :active-text="activeText"
      :inactive-text="inactiveText"
      :inline-prompt="inlinePrompt"
      :loading="loading"
      :disabled="disabled"
    />
    <!-- <br />
    <slot name="footer" /> -->
  </div>
</template>

<script setup>
const props = defineProps({
  value: {
    type: Boolean,
    required: true,
  },
  activeText: String,
  inactiveText: String,
  size: String,
  disabled: {
    type: Boolean,
    default: false,
  },
  inlinePrompt: {
    type: Boolean,
    default: false,
  },
  loading: {
    type: Boolean,
    default: false,
  },
});

const switchValue = ref(null);
switchValue.value = props.value;
</script>
