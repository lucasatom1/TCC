<template>
  <v-row class="align-center mediumPurple rounded">
    <v-col cols="12" sm="6" md="3">
      <p>Dispositivo selecionado</p>
    </v-col>
    <v-col cols="12" sm="6" md="9">
      <v-text-field></v-text-field>
    </v-col>

    <v-col cols="12" sm="6" md="3">
      <v-text-field label="Profissional"></v-text-field>
    </v-col>
    <v-col cols="12" sm="6" md="3">
      <v-text-field label="Contato"></v-text-field> </v-col
    ><v-col cols="12" sm="6" md="3">
      <v-text-field label="Telefone"></v-text-field> </v-col
    ><v-col cols="12" sm="6" md="3">
      <v-text-field label="Fax"></v-text-field>
    </v-col>

    <v-col cols="12" sm="6" md="4">
      <v-text-field label="Fabricante"></v-text-field>
    </v-col>
    <v-col cols="12" sm="6" md="4">
      <v-text-field label="Modelo"></v-text-field> </v-col
    ><v-col cols="12" sm="6" md="4">
      <v-text-field label="Data de entrega"></v-text-field>
    </v-col>

    <v-col cols="12" sm="6" md="3">
      <v-text-field label="Custo"></v-text-field>
    </v-col>
    <v-col cols="12" sm="6" md="3">
      <v-text-field label="Financiador"></v-text-field> </v-col
    ><v-col cols="12" sm="6" md="6">
      <v-text-field label="Notas / Documentações"></v-text-field>
    </v-col>

    <v-col cols="12" sm="6" md="6">
      <v-text-field
        label="Quanto tempo o dispositivo atenderá às necessidades da pessoa em Anos"
      ></v-text-field>
    </v-col>
    <v-col cols="12" sm="6" md="3">
      <v-text-field label="Meses"></v-text-field> </v-col
    ><v-col cols="12" sm="6" md="3">
      <v-text-field label="Semanas"></v-text-field>
    </v-col>
  </v-row>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.mediumPurple {
  background-color: rgb(205, 192, 218);
}
</style>