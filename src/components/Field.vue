<script setup lang="ts">
const props = defineProps({
  as: {
    type: String,
    required: true,
  },
  name: {
    type: String,
    required: true,
  },
})

const state = reactive({
  value: '',
})
</script>

<template>
  <div>
    <label :for="props.name">{{ props.name }}</label>
    <input v-model="state.value" :type="props.as" :name="props.name">
  </div>
</template>
