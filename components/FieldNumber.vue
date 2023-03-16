<template>
  <div v-if="reference === 'INTEGER'">
    <slot name="header" />
    <br />
    <el-input-number
      v-model="numValue"
      :min="min"
      :max="max"
      :step="step"
      :step-strictly="stepStrictly"
      :controls="controls"
      :disabled="disabled"
      :placeholder="placeholder"
      :controls-position="controlsPosition"
      :size="sizes"
      style="width: 100%"
      @change="handleChange"
      @focus="isFocus"
    />
    <br />
    <slot name="footer" />
  </div>
  <div v-else-if="reference === 'AMOUNT'">
    <slot name="header" />
    <br />
    <el-input-number
      v-show="currentFocust"
      v-model="numValue"
      ref="FieldNumberAmount"
      :min="min"
      :max="max"
      :autofocus="true"
      :focus="true"
      :step="step"
      :step-strictly="stepStrictly"
      :precision="precision"
      :controls="controls"
      :disabled="disabled"
      :placeholder="placeholder"
      :controls-position="controlsPosition"
      :size="sizes"
      style="width: 100%"
      @change="handleChange"
      @focus="isFocus"
      @blur="isBlur"
    />
    <el-input
      v-show="!currentFocust"
      v-model="amount"
      :disabled="disabled"
      :placeholder="placeholder"
      @focus="isFocus"
    />
    <br />
    <slot name="footer" />
  </div>
  <div v-else-if="reference === 'QUANTITY'">
    <slot name="header" />
    <br />
    <el-input-number
      v-model="numValue"
      :min="min"
      :max="max"
      :step="step"
      :step-strictly="stepStrictly"
      :precision="precision"
      :controls="controls"
      :disabled="disabled"
      :placeholder="placeholder"
      :controls-position="controlsPosition"
      :size="sizes"
      style="width: 100%"
      @change="handleChange"
      @focus="isFocus"
    />
    <br />
    <slot name="footer" />
  </div>
</template>
<script lang="ts" setup>
import { ref, computed } from 'vue';
const props = defineProps({
  num: Number,
  valueType: {
    type: String,
    default: '',
  },
  min: {
    type: Number,
    default: -Infinity,
  },
  max: {
    type: Number,
    default: Infinity,
  },
  step: {
    type: Number,
    default: 1,
  },
  stepStrictly: {
    type: Boolean,
    default: false,
  },
  precision: {
    type: Number,
    default: 2,
  },
  size: {
    type: String,
    default: 'default',
  },
  controls: {
    type: Boolean,
    default: true,
  },
  disabled: {
    type: Boolean,
    default: false,
  },
  controlsPosition: {
    type: String,
    default: 'default',
  },
  slotsCurrency: {
    type: String,
    default: '$',
  },
  placeholder: String,
});

/**
 * Ref
 *  @FieldNumberAmount -> @params {HTMLInputElement | Null} -> Template refs should be created with an explicit generic type argument @DefaultVAlue -> null
 *  @currentFocust -> @params {Boolean} -> Value of the flag that activates the focus @DefaultValue -> false
 */
const FieldNumberAmount = ref(null);

const currentFocust = ref(false);

/**
 * Computed
 *  @amount
 *  @currentValueType
 *  @reference
 *  @numValue
 *  @slot
 */

const amount = computed({
  // getter
  get() {
    return slot.value + numValue.value;
  },
  // setter
  set(newValue) {
    return newValue;
  },
});

const currentValueType = computed(() => {
  return props.valueType;
});

const reference = computed(() => {
  let type = 'INTEGER';
  switch (currentValueType.value) {
    case 'ID':
      type = 'INTEGER';
      break;
    case 'INTEGER':
      type = 'INTEGER';
      break;
    case 'NUMBER':
      type = 'QUANTITY';
      break;
    case 'QUANTITY':
      type = 'QUANTITY';
      break;
    case 'AMOUNT':
      type = 'AMOUNT';
      break;
    case 'COSTS_PLUS_PRICES':
      type = 'AMOUNT';
      break;
  }
  return type;
});

const numValue = computed(() => {
  return props.num;
});

const slot = computed(() => {
  return props.slotsCurrency;
});

/**
 * Methods
 * @isFocus -> @params {Boolean} -> triggers when Input focuses
 * @isBlur -> @params {Boolean} -> triggers when Input blurs
 * @handleChange -> @params {Number} -> triggers when the value changes
 */

const isFocus = (focus: boolean) => {
  FieldNumberAmount.value.focus();
  currentFocust.value = true;
};
const isBlur = (blur: boolean) => {
  currentFocust.value = false;
};

const handleChange = (value: number) => {
  console.log(value);
};
</script>

<style>
.el-input-number .el-input__inner {
  line-height: 1;
  text-align: right;
}
.el-input .el-input__inner {
  line-height: 1;
  text-align: right;
}
</style>
