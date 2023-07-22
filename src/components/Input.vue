<script setup lang="ts">
import { ref } from "vue";
const message = ref("");

defineProps<{
  visibility: boolean;
}>();

const emit = defineEmits(["addUser", "hide"]);
const hideContacts = (visibility: boolean) => {
  emit("hide", visibility);
};
const handleSubmit = (name: string) => {
  emit("addUser", name);
  message.value = "";
};
</script>

<template>
  <input v-model="message" placeholder="type smth" />
  <button class="btn" @click="handleSubmit(message)">Add</button>
  <button class="btn" @click="hideContacts(!visibility)">
    {{ visibility ? "Show all" : "Hide chosen" }}
  </button>
</template>

<style>
.btn {
  margin-left: 5px;
}
</style>
