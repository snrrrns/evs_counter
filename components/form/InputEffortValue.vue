<template>
  <div class="w-1/3">
    <label class="block font-medium mb-2">{{ label }}</label>
    <input
      :value="effortValue"
      @blur="updateEffortValue"
      type="number"
      min="0"
      max="252"
      class="w-full border border-gray-300 rounded-md py-2 px-3 mb-4"
    />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

type EffortValue = {
  effortValue: string,
};

export default defineComponent({
  props: {
    label: {
      type: String,
      required: true,
    },
    modelValue: {
      type: String,
      required: true,
    }
  },
  data(): EffortValue {
    return {
      effortValue: this.modelValue,
    };
  }, 
  watch: {
    /**
     * 努力値の文字列を監視し、
     * 不正な値の場合は整形する
     *
     * @param {string} newVal 入力された努力値
     * @return {void}
     */
    effortValue(newVal: string) {
      let result = newVal;
      const zeroStartPattern = /0{1,}\d{1,}$/;
      const floatPattern = /\d*\.\d+$/;

      if (newVal === '' || parseInt(newVal) < 0) {
        result = '0';
      } else if (parseInt(newVal) > 252) {
        result = '252';
      } else if (zeroStartPattern.test(newVal)) {
        result = parseInt(newVal, 10).toString();
      } else if (floatPattern.test(newVal)) {
        const intPart = Math.floor(parseFloat(newVal));
        result = intPart.toString();
      }

      this.effortValue = result;
      this.$emit('update:modelValue', this.effortValue);
    },
  },
  methods: {
    updateEffortValue(event: FocusEvent) {
      const newValue = (event.target as HTMLInputElement).value

      this.effortValue = newValue;
      this.$emit('update:modelValue', this.effortValue);
    },
  }
});
</script>
