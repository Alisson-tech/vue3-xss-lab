<template>
    <v-app>
      <v-container>
        <!-- Formulário -->
        <v-row align="center" justify="space-between">
          <v-col cols="12" md="8">
            <v-text-field
              v-model="newName"
              label="Digite um nome"
              outlined
              clearable
            ></v-text-field>
          </v-col>
          <v-col cols="12" md="4">
            <v-btn color="primary" @click="addName">{{$t('add')}}</v-btn>
          </v-col>
        </v-row>
  
        <!-- Tabela -->
        <v-data-table
          :headers="headers"
          :items="names"
          class="mt-4"
          dense
          disable-pagination
          disable-sort
        >
          <template v-slot:body="{ items }">
            <tr v-for="item in items" :key="item.id">
              <td>{{ item.id }}</td>
              <td>{{ item.name }}</td>
              <td>
                <v-btn
                  color="error"
                  small
                  text
                  @click="removeName(item.id)"
                >
                {{$t('remove')}}
                </v-btn>
              </td>
              <dialog-vulnerability v-model="dialogDeleted" :itemName="item.name" @close="closeDialog"/>
              <!-- <dialog-fix v-model="dialogDeleted" :itemName="item.name" @close="closeDialog"/> -->
            </tr>
          </template>
        </v-data-table>
      </v-container>
    </v-app>
  </template>
  
  <script>
  import DialogVulnerability from './DialogVulnerability.vue';
  // import DialogFix from './DialogFix.vue';

  export default {
    data() {
      return {
        newName: "", 
        names: [], 
        dialogDeleted: false,
        headers: [
          { text: "ID", align: "start", sortable: false, value: "id" },
          { text: "Nome", sortable: false, value: "name" },
          { text: "Ações", sortable: false, value: "actions" },
        ],
      };
    },
    components: {
      DialogVulnerability,
      // DialogFix,
    },
    methods: {
      addName() {
        if (this.newName.trim()) {
          this.names.push({
            id: this.names.length + 1,
            name: this.newName,
          });
          this.newName = ""; 
        } else {
          alert("O campo Nome não pode estar vazio.");
        }
      },
      removeName() {
        this.dialogDeleted = true;
      },
      closeDialog(value) {
        this.dialogDeleted = value;
      },
    },
  };
  </script>
  
  <style scoped>
  /* Ajustes de estilo */
  .v-btn {
    margin-top: 16px;
  }
  </style>
  