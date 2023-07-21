<script setup lang="ts">
import { ref } from "vue";

defineProps<{ msg: string }>();

const increment = () => {
  count.value++;
};

const count = ref(0);
</script>

<template>
  <div class="card">
    <button type="button" @click="increment">count is {{ count }}</button>
  </div>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
