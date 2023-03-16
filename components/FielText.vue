<template>
  <div>
    <slot name="header" />
    <br />
    <el-input
      v-model="input"
      :type="type"
      :size="sizes"
      :show-word-limit="showWordLimit"
      :show-password="showPassword"
      :rows="rows"
      :placeholder="placeholder"
      :maxlength="maxlength"
      :minlength="minlength"
      :clearable="clearable"
      :disabled="disabled"
      :autosize="autosize"
    />
    <!-- <slot name="content" /> -->
    <!-- <el-input> {{ text }} {{ typeof text }} <slot name="content" /> </el-input> -->
    <br />
    <slot name="footer" />
  </div>
</template>

<script setup>
const props = defineProps({
  type: {
    type: String,
    required: true,
  },
  text: String | Number,
  sizes: String,
  rows: {
    type: Number,
    default: 2,
  },
  placeholder: String,
  type: String,
  maxlength: String | Number,
  minlength: Number,
  showPassword: {
    type: Boolean,
    default: false,
  },
  showWordLimit: {
    type: Boolean,
    default: false,
  },
  clearable: {
    type: Boolean,
    default: false,
  },
  disabled: {
    type: Boolean,
    default: false,
  },
  autosize: {
    type: Boolean,
    default: false,
  },
});
const input = ref('');
input.value = props.text;
</script>
