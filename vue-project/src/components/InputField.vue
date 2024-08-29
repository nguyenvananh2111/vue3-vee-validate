<template>
  <div class="base-input-wrapper">
    <Field :name="props.name" v-slot="{ field, errors }">
      <BaseInput v-bind="field" v-model="field.value" :label="props.label" :required="props.required"/>
      <p class="has-error">{{ errors }}</p>
    </Field>
  </div>
</template>

<script setup>
import { Field } from 'vee-validate';
import BaseInput from "@/components/BaseInput.vue";
const props = defineProps({
  label: String,
  required: Boolean,
  name: String
});
</script>

<style lang="scss">
.base-input-wrapper {
  .has-error {
    color: red;
  }
}
</style>