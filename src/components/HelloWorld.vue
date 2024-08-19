<template>
  <div>
    <div class="inline-inputs">
      <input
        type="date"
        v-model="localTradeForm.dataLiquidacao"
      />
      <input
        type="date"
        v-model="localTradeForm.dataOperacao"
      />
    </div>
    <div class="extra-field">
      <!-- Input para uma propriedade que não está na interface -->
      <input
        type="text"
        v-model="localTradeForm.extraField"
        placeholder="Campo Extra"
      />
    </div>
  </div>
</template>

<script setup lang="ts">
import { computed, defineProps, defineEmits } from 'vue';
import { ITradeForm } from './ITradeForm.ts';

const props = defineProps<{
  modelValue: ITradeForm;
}>();

const emit = defineEmits<{
  (event: 'update:modelValue', value: ITradeForm): void;
}>();

const localTradeForm = computed({
  get: () => props.modelValue,
  set: (value: ITradeForm) => {
    emit('update:modelValue', value);
  }
});
</script>

<style scoped>
.inline-inputs {
  display: flex;
  gap: 10px;
  margin-bottom: 20px;
}
.extra-field {
  margin-top: 20px;
}
</style>
