<template>
  <v-row class="">
    <v-card width="400px" class="d-flex align-center justify-center">
      <v-card-item class="">
        <v-col cols="6">
          <v-card
            variant="tonal"
            color="success"
            class="elevation-2 align-center text-center pb-4 font-weight-black"
            min-width="150px"
            title="Lucro"
          >
            <span>+{{ lucro }}R$</span>
          </v-card>
        </v-col>
      </v-card-item>

      <v-card-item class="">
        <v-col cols="6">
          <v-card
            variant="tonal"
            color="error"
            class="elevation-2 align-center text-center pb-4 font-weight-black"
            min-width="150px"
            title="Despesas"
          >
            <span>{{ despesas }}R$</span>
          </v-card>
        </v-col>
      </v-card-item>
    </v-card>
  </v-row>
</template>

<script setup>
import { defineProps } from "vue";

const props = defineProps({
  lucro: Number,
  despesas: Number,
});
</script>
