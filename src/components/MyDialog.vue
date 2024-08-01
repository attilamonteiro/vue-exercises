<template>
  <div v-if="show" class="dialog-overlay">
    <div class="dialog-box">
      <header class="dialog-header">
        <h3>{{ title }}</h3>
        <button @click="close">X</button>
      </header>
      
      <div class="dialog-body">
        <slot name="body">Default body content</slot>
      </div>
      
      <footer class="dialog-footer">
        <!-- Renderiza o slot "footer" se existir, caso contrário, renderiza o botão de confirmar -->
        <template v-if="slots.footer">
          <slot name="footer" />
        </template>
        <template v-else>
          <button @click="confirm">{{ btnLabel }}</button>
        </template>
      </footer>
    </div>
  </div>
</template>

<script setup lang="ts">
import { computed, useSlots } from 'vue';

const props = defineProps<{
  show: boolean;
  title: string;
  btnLabel?: string;
}>();

const emit = defineEmits(['close', 'confirm']);

const slots = useSlots();

const btnLabel = computed(() => props.btnLabel || 'Confirm');

function close() {
  emit('close');
}

function confirm() {
  emit('confirm');
}
</script>

<style scoped>
.dialog-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
}

.dialog-box {
  background: white;
  border-radius: 8px;
  width: 300px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  display: flex;
  flex-direction: column;
}

.dialog-header {
  padding: 10px;
  background: #f0f0f0;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.dialog-body {
  padding: 20px;
}

.dialog-footer {
  padding: 10px;
  display: flex;
  justify-content: flex-end;
  background: #f0f0f0;
}
</style>
