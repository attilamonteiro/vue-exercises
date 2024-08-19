<template>
  <div>
    <TradeFormComponent v-model:modelValue2="tradeFormData" />
    <AnotherComponent />
  </div>
</template>

<script setup lang="ts">
import { ref, provide } from 'vue';
import TradeFormComponent from './components/HelloWorld.vue';
import { ITradeForm } from './components/ITradeForm';
import AnotherComponent from './components/AnotherComponent.vue';

const tradeFormData = ref<ITradeForm>({
  dataLiquidacao: null,
  dataOperacao: null,
  extraField: 'veio'
});

provide('tradeFormData', tradeFormData);
</script>
