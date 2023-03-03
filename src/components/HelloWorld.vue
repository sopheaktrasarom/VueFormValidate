<script setup lang="ts">
import { ref } from "vue";
const props = defineProps<{ msg: string; name: string }>();
const num = ref(0);
</script>

<template>
  <p>{{ props.msg }}</p>
  <p>{{ props.name }}</p>
  <p>{{ num }}</p>
  <slot name="Hello"></slot>
</template>
