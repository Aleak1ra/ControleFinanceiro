<template>
  <div>
    <Header />
    <Balance :total="total" />
    <Painel :lucro="lucro" :despesas="despesas" />
    <Historico :items="items" />
    <AddNewTransaction @submit-item="handleSubmitItem" />
  </div>
</template>

<script setup>
import { computed, ref, defineProps } from "vue";
import AddNewTransaction from "./components/AddNewTransaction.vue";
import Balance from "./components/Balance.vue";
import Header from "./components/Header.vue";
import Historico from "./components/Historico.vue";
import Painel from "./components/Painel.vue";
const total = computed(() => {
  return items.value.reduce((acc, item) => acc + item.valor, 0);
});
const lucro = computed(() => {
  return items.value
    .filter((item) => item.valor > 0)
    .reduce((acc, item) => acc + item.valor, 0);
});
const despesas = computed(() => {
  return items.value
    .filter((item) => item.valor <= 0)
    .reduce((acc, item) => acc + item.valor, 0);
});
const handleSubmitItem = (item) => {
  items.value.push(item);
};
const items = ref([
  {
    title: "Item 1",
    description: "Lorem ipsum dolor sit amet, consectetur adipiscing elit...",
    valor: 20,
  },
  {
    title: "Item 2",
    description: "Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua...",
    valor: 0,
  },
  {
    title: "Item 3",
    description: "Lorem ipsum dolor sit amet, consectetur adipiscing elit...",
    valor: 200,
  },
  {
    title: "Item 4",
    description: "Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua...",
    valor: -15,
  },
  {
    title: "Item 5",
    description: "Lorem ipsum dolor sit amet, consectetur adipiscing elit...",
    valor: 200,
  },
  {
    title: "Item 6",
    description: "Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua...",
    valor: 0,
  },
  {
    title: "Item 1",
    description: "Lorem ipsum dolor sit amet, consectetur adipiscing elit...",
    valor: 200,
  },
  {
    title: "Item 2",
    description: "Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua...",
    valor: 0,
  },
  {
    title: "Item 3",
    description: "Lorem ipsum dolor sit amet, consectetur adipiscing elit...",
    valor: 200,
  },
  {
    title: "Item 4",
    description: "Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua...",
    valor: 0,
  },
  {
    title: "Item 5",
    description: "Lorem ipsum dolor sit amet, consectetur adipiscing elit...",
    valor: 200,
  },
  {
    title: "Item 6",
    description: "Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua...",
    valor: 0,
  },
]);
</script>
