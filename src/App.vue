<script setup lang="ts">
import HelloWorld from "./components/HelloWorld.vue";
import List from "./components/List.vue";
import Input from "./components/Input.vue";
import { ref, computed, watch } from "vue";

const contacts = ref([
  { id: 1, name: "Bohdan", email: "bdn@gmail.com", done: true },
  { id: 2, name: "John", email: "bdn@gmail.com", done: true },
  { id: 3, name: "Bill", email: "bdn@gmail.com", done: false },
]);

const hideCompleted = ref(false);

const filteredContacts = computed(() => {
  return hideCompleted.value
    ? contacts.value.filter((el) => !el.done)
    : contacts.value;
});

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

const hide = (visibility: boolean) => {
  hideCompleted.value = visibility;
};

async function fetchData() {
  const res = await fetch(`https://api.adviceslip.com/advice`);
  const result = await res.json();
  console.log(result);
}

fetchData();
</script>

<template>
  <HelloWorld msg="Vite + Vue" />
  <Input @addUser="addUser" :visibility="hideCompleted" @hide="hide" />
  <List :data="filteredContacts" @deleteUser="handleUserDelete" />
</template>

<style scoped></style>
