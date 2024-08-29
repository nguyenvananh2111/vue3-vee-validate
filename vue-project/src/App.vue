<template>
  <div>
    <div :style="{ border: '1px solid red' }">
      <Form1 />
    </div>
    <div :style="{ border: '1px solid red' }">
      <Form2 />
    </div>
  </div>
</template>
<script setup>
import Form1 from "@/components/Form1.vue";
import Form2 from "@/components/Form2.vue";
</script>
<style scoped></style>
