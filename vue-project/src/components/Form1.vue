<template>
  <form @submit="onSubmit">
    <InputField label="Email" required name="email" />
    <InputField label="ConfirmEmail" required name="confirmEmail" />
    <Button type="submit" label="Submit"></Button>
  </form>
</template>
<script setup>
import { ref } from "vue";
import { useForm, useField } from "vee-validate";

import InputField from "@/components/InputField.vue";

const isEmail = (value) => {
  return /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(value);
};

const { handleSubmit, values } = useForm({
  initialValues: {
    email: "anh@example.com",
    confirmEmail: "anh@example.com",
  },
  validationSchema: {
    email: (val) => {
      if (val.trim() === "") {
        return "Please fill in the email";
      }
      if (!isEmail(val)) {
        return "Invalid email";
      }
      return true;
    },
    confirmEmail: (val) => {
      if (val.trim() === "") {
        return "Please fill in the email";
      }
      if (val !== values.email) {
        return "Confirm email is different with email";
      }
      return true;
    },
  },
});

const onSuccess = (values) => {
  console.log("onSuccess", values);
};

const onInvalidSubmit = ({ values, errors, results }) => {
  console.log("onInvalidSubmit", {
    values,
    errors,
    results,
  });
};

const onSubmit = handleSubmit(onSuccess, onInvalidSubmit);
</script>
<style scoped></style>
