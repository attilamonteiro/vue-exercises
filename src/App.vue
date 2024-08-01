<template>
  <div>
    <button @click="showDialog = true">Open Dialog</button>
    <button @click="toggleFooter">Toggle Footer</button>

    <MyDialog :show="showDialog" title="My Custom Dialog" @close="showDialog = false" @confirm="handleConfirm">
      <template #body>
        <p>This is custom body content.</p>
      </template>
      <!-- Condicionalmente renderiza o slot footer se showFooter for verdadeiro -->
      <template v-if="showFooter" #footer>
        <button @click="handleFooterClick">Custom Footer Button</button>
      </template>
    </MyDialog>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import MyDialog from './components/MyDialog.vue';

const showDialog = ref(false);
const showFooter = ref(false);

function handleConfirm() {
  alert('Confirmed!');
  showDialog.value = false;
}

function handleFooterClick() {
  alert('Footer button clicked!');
}

function toggleFooter() {
  showFooter.value = !showFooter.value;
}
</script>
