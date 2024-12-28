<template>
  <v-container>
    <v-row>
      <v-col cols="12">
        <h1>Calcule o seu IMC</h1>
      </v-col>
    </v-row>
    
    <v-row>
      <v-col cols="12">
        <v-text-field v-model="peso" label="Digite o seu peso" required />
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="12">
        <v-text-field v-model="altura" label="Digite a sua altura" required />
      </v-col>
    </v-row>

    <v-row>
      <v-col cols="12">
        <v-btn density="default" color="indigo-darken-3" @click="calcularIMC()">
          Calcular
        </v-btn>
      </v-col>
    </v-row>
    <DialogComponent :valortotal="resultado" />

    <v-row>
      <v-col cols="12">
        <v-text-field v-model="nome" label="Digite um nome:" required />
      </v-col>
    </v-row>
    <TableComponent :nomeDaTabela = "nome"/>
  </v-container>
</template>

<script>

export default {
  data() {
    return {
      peso: 0,
      altura: 0,
      resultado: 0,
      nome: "",
      resposta: "",
    };
  },
  methods: {
    calcularIMC() {
      this.resultado = this.peso / (this.altura * this.altura);
    },
    
  },
};
</script>