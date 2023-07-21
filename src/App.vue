<script setup lang="ts">
import HelloWorld from "./components/HelloWorld.vue";
import List from "./components/List.vue";
import Input from "./components/Input.vue";
import { ref } from "vue";

const contacts = ref([
  { id: 1, name: "Bohdan", email: "bdn@gmail.com", done: true },
  { id: 2, name: "John", email: "bdn@gmail.com", done: true },
  { id: 3, name: "Bill", email: "bdn@gmail.com", done: false },
]);

const handleUserDelete = (id: number) => {
  contacts.value = contacts.value.filter((contact) => contact.id !== id);
};

const addUser = (name: string) => {
  contacts.value.push({
    id: 4,
    name: name,
    email: name + "@gmail.com",
    done: false,
  });
};
</script>

<template>
  <HelloWorld msg="Vite + Vue" />
  <Input @addUser="addUser" />
  <List :data="contacts" @deleteUser="handleUserDelete" />
</template>

<style scoped></style>
