<template>
  <div class="text-center pa-4">
    <v-btn @click="dialog = true"> Open Dialog </v-btn>

    <v-dialog v-model="dialog" width="auto">
      <v-card
        max-width="400"
        prepend-icon="mdi-update"
        :text="'Valor Total IMC: ' + valorTotalImc"
        title="Update in progress"
      >
        <template 
            v-slot:actions>
          <v-btn 
          class="ms-auto" 
          text="Ok" 
            @click="dialog = false"
          />
        </template>
      </v-card>
    </v-dialog>
  </div>
</template>
  <script>
export default {
  name: "DialogComponent",
  props: {
    valortotal: Number,
  },
  data() {
    return {
      dialog: false,
    };
  },
  computed: {
    valorTotalImc() {
      return this.valortotal;
    },
  },
};
</script>