<script setup>
</script>

<template>
  <div>
    <Formik
      v-slot="{ values, errors, handleSubmit, isSubmitting }"
      :initial-values="{ name: '' }"
      :validate="values => {
        const errors = {
          name: '',
        }
        if (!values.name) {
          errors.name = 'Required'
        }
        return errors
      }"
      :on-submit="(values, actions) => {
        setTimeout(() => {
          alert(JSON.stringify(values, null, 2));
          actions.setSubmitting(false);
        }, 1000);
      }"
    >
      <form @submit="handleSubmit(values)">
        <Field v-model="values.name" as="text" name="text" />
        <div v-if="errors.name">
          {{ errors.name }}
        </div>
        <button type="submit" :disabled="isSubmitting">
          Submit
        </button>
      </form>
    </Formik>
  </div>
</template>

