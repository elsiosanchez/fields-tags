<template>
  <el-card class="box-card">
    <el-date-picker
      v-model="fieldValue"
      :type="valueDate"
      :placeholder="placeholder"
      :format="format"
      :shortcuts="shortcuts"
      :start-placeholder="startPlaceholder"
      :end-placeholder="endPlaceholder"
      :disabled="disabled"
      :clearable="clearable"
      :size="size"
    />
  </el-card>
</template>

<script setup>
const props = defineProps({
  valueDate: {
    type: String,
    required: false,
  },
  format: {
    type: String,
    default: 'YYYY-MM-DD',
    required: false,
  },
  valueDate: {
    type: String,
    default: 'date',
    required: true,
  },
  shortcuts: Array,
  placeholder: String,
  startPlaceholder: String,
  endPlaceholder: String,
  disabled: Boolean,
  clearable: {
    type: Boolean,
    default: true,
  },
  size: {
    type: String,
    default: 'default',
  },
});
const fieldValue = ref('');
fieldValue.value = props.valueDate;
</script>
