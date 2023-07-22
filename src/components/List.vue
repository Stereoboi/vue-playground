<script setup lang="ts">
defineProps<{
  data: Array<{ id: number; name: string; email: string; done: boolean }>;
}>();
const emit = defineEmits(["deleteUser"]);
const handleDelete = (id: number) => emit("deleteUser", id);
</script>

<template>
  <li class="list-items text" v-for="el in data" :key="el.id">
    <input type="checkbox" v-model="el.done" />
    <p class="text">{{ el.name }}</p>
    <p class="text">{{ el.email }}</p>
    <button class="btn" @click="handleDelete(el.id)">Delete</button>
  </li>
</template>

<style>
.list-items {
  display: flex;
  justify-content: space-between;
}
.btn {
  margin-left: 10px;
}
.text {
  padding: 5px;
}
</style>
