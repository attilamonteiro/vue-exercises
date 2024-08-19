<template>
  <div>
    <TradeFormComponent
      :modelValue="tradeFormData"
      @update:modelValue="updateTradeForm"
    />
    <AnotherComponent />
  </div>
</template>

<script setup lang="ts">
import { ref, provide } from 'vue';
import TradeFormComponent from './components/HelloWorld.vue';
import { ITradeForm } from './components/ITradeForm';
import AnotherComponent from './components/AnotherComponent.vue';

// Define o estado inicial do tradeForm
const tradeFormData = ref<ITradeForm>({
  dataLiquidacao: null,
  dataOperacao: null,
  extraField: 'veio'
});

// Fornece os dados para todos os componentes descendentes
provide('tradeFormData', tradeFormData);

// Atualiza o estado do tradeForm
function updateTradeForm(newValue: ITradeForm) {
  tradeFormData.value = newValue;
}
</script>
