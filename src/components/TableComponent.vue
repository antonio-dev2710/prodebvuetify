<template>
  <v-table height="300px" fixed-header>
    <thead>
      <tr>
        <th class="text-left">Nome</th>
        <th class="text-left">Região</th>
        <th class="text-left">Frequencia</th>
        <th class="text-left">Rank</th>
        <th class="text-left">Sexo</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="item in listaDeInfoIBGE" :key="item.nome">
        <td>{{ item.nome }}</td>
        <td>{{ item.regiao }}</td>
        <td>{{ item.freq }}</td>
        <td>{{ item.rank }}</td>
        <td>{{ item.sexo }}</td>
      </tr>
    </tbody>
  </v-table>

  <v-btn class="mt-4" @click="obterDadosFiltroNome()"> Obter nome </v-btn>
</template>
  <script>
import axios from "axios";
export default {
  name: "TableComponent",
  props: {
    nomeDaTabela: String ?? "",
  },
  data() {
    return {
      desserts: [
        {
          name: "Frozen Yogurt",
          calories: 159,
        },
        {
          name: "Ice cream sandwich",
          calories: 237,
        },
        {
          name: "Eclair",
          calories: 262,
        },
        {
          name: "Cupcake",
          calories: 305,
        },
        {
          name: "Gingerbread",
          calories: 356,
        },
        {
          name: "Jelly bean",
          calories: 375,
        },
        {
          name: "Lollipop",
          calories: 392,
        },
        {
          name: "Honeycomb",
          calories: 408,
        },
        {
          name: "Donut",
          calories: 452,
        },
        {
          name: "KitKat",
          calories: 518,
        },
      ],
      listaDeInfoIBGE: Array ?? [],
    };
  },
  mounted() {
    this.obterDados();
  },
  methods: {
        obterDadosFiltroNome() {
            if(!this.nomeDaTabela){
            this.obterDados()
            }
            else{
                this.listaDeInfoIBGE = this.listaDeInfoIBGE.filter(
                (dadoPessoa) => dadoPessoa.nome == this.nomeDaTabela
            );}
            
        
        
        },
        async obterDados() {
      const endpoint = `https://servicodados.ibge.gov.br/api/v2/censos/nomes`;
      debugger;
      await axios.get(endpoint).then((response) => {
       this.listaDeInfoIBGE = response.data
      });
    },
    },
};
</script>