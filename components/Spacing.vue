<script setup lang="ts">
import {ref} from "vue";
const props = defineProps({
  amount: {
    default: 1,
  },
});

const amount = ref(props.amount);
const amount2 = String(props.amount) + "px";
</script>

<template></template>
