<template>
    <div>
      <p>Data de Liquidação: {{ tradeFormData?.dataLiquidacao }}</p>
      <p>Data de Operação: {{ tradeFormData?.dataOperacao }}</p>
      <p>Campo Extra: {{ tradeFormData?.extraField }}</p>
    </div>
  </template>
  
  <script setup lang="ts">
  import { inject } from 'vue';
  import { ITradeForm } from './ITradeForm.ts';
  import { Ref } from 'vue';
  
  // Injeta o valor fornecido pelo provider
  const tradeFormData = inject<Ref<ITradeForm>>('tradeFormData');
  </script>
  