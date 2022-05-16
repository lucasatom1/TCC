<template>
  <div>
    <v-stepper v-model="step" vertical>
      <v-stepper-step :complete="step > 1" step="1">
        Formulário Cliente
        <small>Inicial 1 de 2</small>
      </v-stepper-step>
      <v-stepper-content step="1">
        <Form1 />
        <v-btn color="primary" @click="step = 2"> Continuar </v-btn>
      </v-stepper-content>

      <v-stepper-step :complete="step > 2" step="2">
        Formulário do Dispositivo <small>Inicial 2 de 2</small>
      </v-stepper-step>
      <v-stepper-content step="2">
        <Form2 />
        <v-btn color="primary" @click="step = 3"> Continuar </v-btn>
        <v-btn text @click="step = 1"> Voltar </v-btn>
      </v-stepper-content>

    </v-stepper>
  </div>
</template>

<script>
import Form1 from "./Form1";
import Form2 from "./Form2";

export default {
  components: {
    Form1,
    Form2
  },
  name: "FormPage1",
  data() {
    return {
      step: 1,
   
    };
  },
};
</script>

<style lang="scss" scoped>
</style>