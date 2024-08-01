<script setup>
import { toRefs, computed } from 'vue'

const props = defineProps({
  firstName: String,
  lastName: String
})

const emit = defineEmits(['update:firstName', 'update:lastName'])

const { firstName, lastName } = toRefs(props)

const localFirstName = computed({
  get: () => firstName.value,
  set: value => emit('update:firstName', value)
})

const localLastName = computed({
  get: () => lastName.value,
  set: value => emit('update:lastName', value)
})
</script>

<template>
  <div>
    <input type="text" v-model="localFirstName" placeholder="First Name" />
    <input type="text" v-model="localLastName" placeholder="Last Name" />
    <!-- Slot para conteúdo adicional -->
    <slot></slot>
  </div>
</template>
