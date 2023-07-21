<script setup lang="ts">
import { ref } from "vue";

const items = ref(["My", "name", "is", "Bohdan"]);
</script>

<template>
  <li class="list-items" v-for="el in items">{{ el }}</li>
</template>

<style>
.list-items {
  display: flex;
}
</style>
