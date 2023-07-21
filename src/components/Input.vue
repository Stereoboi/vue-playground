<script setup lang="ts">
import { ref } from "vue";
const message = ref("");
const emit = defineEmits(["addUser"]);
const handleSubmit = (name: string) => {
  emit("addUser", name);
  message.value = "";
};
</script>

<template>
  <input v-model="message" placeholder="type smth" />
  <button class="btn" @click="handleSubmit(message)">Add</button>
</template>

<style>
.btn {
  margin-left: 5px;
}
</style>
