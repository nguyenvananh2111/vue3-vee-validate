<template>
  <div class="base-input-wrapper">
    <p>{{ props.label }} : <span class="has-error">{{ props.required ? '*' : '' }}</span></p>
    <InputText v-bind="{ ...inputProps, ...$attrs }" />
  </div>
</template>

<script setup>
const props = defineProps({
  label: String,
  required: Boolean,
  inputProps: Object
});
</script>

<style lang="scss">
.base-input-wrapper {
  .has-error {
    color: red;
  }
}
</style>
