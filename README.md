# README: Compreendendo o `useSlots` no Vue 3

## O que é `useSlots`?

O `useSlots` é uma função da Composition API do Vue 3 que permite acessar e manipular os slots de um componente. Slots são espaços reservados em um componente que permitem que o conteúdo seja inserido de um componente pai.

## Como Usar `useSlots`

```vue
<template>
  <div>
    <!-- Renderiza o slot "header" se existir -->
    <header v-if="slots.header">
      <slot name="header" />
    </header>
    <!-- Renderiza o slot "body", com conteúdo padrão se o slot não for fornecido -->
    <main>
      <slot name="body">Conteúdo padrão</slot>
    </main>
    <!-- Renderiza o slot "footer" se existir -->
    <footer v-if="slots.footer">
      <slot name="footer" />
    </footer>
  </div>
</template>

<script setup>
import { useSlots } from 'vue';

// Acessa os slots disponíveis no componente
const slots = useSlots();
</script>
