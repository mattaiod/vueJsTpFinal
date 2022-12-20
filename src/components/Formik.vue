<script setup lang="ts">
const props = defineProps({
  initialValues: {
    type: Object,
    required: true,
  },
  validate: {
    type: Function,
    required: false,
    default: () => {},
  },
  onSubmit: {
    type: Function,
    required: false,
    default: () => {},
  },
})

const state = reactive({
  values: props.initialValues,
  errors: {},
  isSumitting: false,
})

const onSubmit = (e: Event) => {
  e.preventDefault()

  state.isSumitting = true

  state.errors = props.validate(state.values)
  if (Object.keys(state.errors).length > 0) {
    state.isSumitting = false
    return
  }

  props.onSubmit(state.values)
  state.isSumitting = false
}
</script>

<template>
  <div>
    FORMIK
    <slot :values="state.values" :errors="state.errors" :handle-submit="onSubmit" :is-submitting="state.isSumitting" />
  </div>
</template>
