<template>
  <div>
    <slot name="header" />
    <br />
    <el-select v-model="select" class="m-2" placeholder="Select" size="large">
      <el-option
        v-for="item in optionList"
        :key="item.value"
        :label="item.label"
        :value="item.value"
        :disabled="item.disabled"
      />
    </el-select>
    <!-- <slot name="content" /> -->
    <!-- <el-input> {{ text }} {{ typeof text }} <slot name="content" /> </el-input> -->
    <br />
    <slot name="footer" />
  </div>
</template>

<script setup>
const props = defineProps({
  value: {
    type: String,
    required: true,
  },
  multiple: {
    type: Boolean,
    default: false,
  },
  collapseTags: {
    type: Boolean,
    default: false,
  },
  collapseTagsTooltip: {
    type: Boolean,
    default: false,
  },
  multipleLimit: {
    type: Number,
    default: 0,
  },
  disabled: {
    type: Boolean,
    default: false,
  },
  clearable: {
    type: Boolean,
    default: false,
  },
  size: {
    type: String,
    default: 'default',
  },
  filterable: {
    type: Boolean,
    default: false,
  },
  allowCreate: {
    type: Boolean,
    default: false,
  },
  noDataText: {
    type: String,
    default: 'No data',
  },
  placeholder: {
    type: String,
    default: 'Select',
  },
  optionList: {
    type: Array,
    required: true,
    default: [
      {
        lable: '',
        value: '',
        disabled: false,
      },
    ],
  },
});
const select = ref('');
select.value = props.value;
</script>
