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
    <component :is="props.as" v-model="state.value" :name="props.name">
      <slot />
    </component>
  </div>
</template>
