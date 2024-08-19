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
      <input
        type="text"
        v-model="localTradeForm.extraField"
        placeholder="Campo Extra"
      />
    </div>
  </div>
</template>

<script setup lang="ts">
import { defineModel } from 'vue';
import { ITradeForm } from './ITradeForm.ts';

const localTradeForm = defineModel<ITradeForm>('modelValue');
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
