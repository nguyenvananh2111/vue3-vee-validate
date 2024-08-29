<template>
  <div>
    <div>
      <Form @submit="onSubmit1">
        <InputField label="Email" required name="email1" />
        <InputField label="ConfirmEmail" required name="confirmEmail1" />
        <Button type="submit" label="Submit"></Button>
      </Form>
    </div>
    <div>
      <Form @submit="onSubmit2">
        <InputField label="Email" required name="email2" />
        <InputField label="ConfirmEmail" required name="confirmEmail2" />
        <Button type="submit" label="Submit"></Button>
      </Form>
    </div>
  </div>
</template>
<script setup>
import { ref } from "vue";
import { useForm, useField, Form } from "vee-validate";

import InputField from "@/components/InputField.vue";

const isEmail = (value) => {
  return /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(value);
};

// Form 1
const { handleSubmit: handleSubmit1, values: values1 } = useForm({
  initialValues: {
    email1: "anh@example.com",
    confirmEmail1: "anh@example.com",
  },
  validationSchema: {
    email1: (val) => {
      if (val.trim() === "") {
        return "Please fill in the email";
      }
      if (!isEmail(val)) {
        return "Invalid email";
      }
      return true;
    },
    confirmEmail1: (val) => {
      if (val.trim() === "") {
        return "Please fill in the email";
      }
      if (val !== values1.email1) {
        return "Confirm email is different with email";
      }
      return true;
    },
  },
});

const onSuccess1 = (values) => {
  console.log("onSuccess1", values);
};

const onInvalidSubmit1 = ({ values, errors, results }) => {
  console.log("onInvalidSubmit1", {
    values,
    errors,
    results,
  });
};

const onSubmit1 = handleSubmit1(onSuccess1, onInvalidSubmit1);

// Form 2
const { handleSubmit: handleSubmit2, values: values2 } = useForm({
  initialValues: {
    email2: "john@example.com",
    confirmEmail2: "john@example.com",
  },
  validationSchema: {
    email2: (val) => {
      if (val.trim() === "") {
        return "Please fill in the email";
      }
      if (!isEmail(val)) {
        return "Invalid email";
      }
      return true;
    },
    confirmEmail2: (val) => {
      if (val.trim() === "") {
        return "Please fill in the email";
      }
      if (val !== values2.email2) {
        return "Confirm email is different with email";
      }
      return true;
    },
  },
});

const onSuccess2 = (values) => {
  console.log("onSuccess2", values);
};

const onInvalidSubmit2 = ({ values, errors, results }) => {
  console.log("onInvalidSubmit2", {
    values,
    errors,
    results,
  });
};

const onSubmit2 = handleSubmit2(onSuccess2, onInvalidSubmit2);
</script>
<style scoped></style>
