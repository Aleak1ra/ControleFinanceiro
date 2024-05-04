<template>
  <v-row>
    <v-card width="400px">
      <v-col>
        <v-card-title>
          <h3 class="text-h5">Adicionar nova transação</h3>
        </v-card-title>
        <v-card-text>
          <v-form @submit.prevent="onSubmit">
            <v-row>
              <v-col cols="12" md="6">
                <v-text-field v-model="produto" label="Título" outlined></v-text-field>
              </v-col>
              <v-col cols="12" md="6">
                <v-text-field
                  v-model="descricao"
                  label="Descrição"
                  outlined
                ></v-text-field>
              </v-col>
              <v-col cols="12" md="6">
                <v-text-field v-model="valor" label="Valor" outlined></v-text-field>
              </v-col>
              <v-col cols="12" md="6">
                <v-select
                  v-model="tipo"
                  :items="['Combustível', 'Lazer', 'Carro']"
                  label="Tipo"
                  outlined
                ></v-select>
              </v-col>
            </v-row>
            <v-card-actions class="d-flex justify-center">
              <v-btn
                class="font-weight-black"
                variant="tonal"
                width="600px"
                color="primary"
                type="submit"
              >
                Salvar
              </v-btn>
            </v-card-actions>
          </v-form>
        </v-card-text>
        <v-divider></v-divider>
      </v-col>
    </v-card>
  </v-row>
</template>

<script setup>
import { ref, defineEmits } from "vue";

const produto = ref("");
const descricao = ref("");
const valor = ref("");
const tipo = ref("");

const emit = defineEmits(["submitItem"]); // Corrigindo o nome do evento para "submitItem"
const onSubmit = () => {
  const newItem = {
    title: produto.value,
    description: descricao.value,
    valor: parseInt(valor.value),
    tipo: tipo.value,
  };
  emit("submitItem", newItem); // Emitindo o evento "submitItem" com o novo item como argumento
};
</script>
