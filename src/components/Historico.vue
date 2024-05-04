<template>
  <v-row>
    <v-card width="400px" class="mt-10">
      <v-card-title class="text-center">Histórico</v-card-title>
      <v-expansion-panels class="mb-6">
        <v-virtual-scroll :items="items" height="400" item-height="48">
          <template v-slot:default="{ item, index }">
            <v-expansion-panel :key="index" class="mt-1">
              <v-expansion-panel-title
                disable-icon-rotate
                @mouseover="showDeleteIcon(index)"
                @mouseleave="hideDeleteIcon(index)"
              >
                {{ item.title }}
                <template v-slot:actions>
                  <span class="flex justify-center align-center ma-1"
                    >R${{ item.valor }}</span
                  >

                  <v-icon :color="iconColor(item.valor)">{{
                    iconName(item.valor)
                  }}</v-icon>
                  <v-icon v-if="showDelete[index]" @click="remover(index)"
                    >mdi-delete</v-icon
                  >
                </template>
              </v-expansion-panel-title>
              <v-expansion-panel-text>
                {{ item.description }}
              </v-expansion-panel-text>
            </v-expansion-panel>
          </template>
        </v-virtual-scroll>
      </v-expansion-panels>
    </v-card>
  </v-row>
</template>

<script setup>
import { ref } from "vue";
import { defineProps } from "vue";

const props = defineProps({
  items: Array,
});

const showDelete = ref([]);

const remover = (index) => {
  props.items.splice(index, 1);
};

const iconName = (valor) => (valor > 0 ? "mdi-check-circle" : "mdi-alert-circle");
const iconColor = (valor) => (valor > 0 ? "green" : "error");

const showDeleteIcon = (index) => {
  showDelete.value[index] = true;
};

const hideDeleteIcon = (index) => {
  showDelete.value[index] = false;
};
</script>
