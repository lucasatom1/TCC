<template>
  <div>
    <v-stepper v-model="step" vertical>
      <v-stepper-step :complete="step > 1" step="1">
        Formulário Cliente
        <small>Inicial 1 de 3</small>
      </v-stepper-step>
      <v-stepper-content step="1">
        <Form5 />
        <v-btn color="primary" @click="step = 2"> Continuar </v-btn>
      </v-stepper-content>

      <v-stepper-step :complete="step > 2" step="2">
        Formulário do Dispositivo <small>Inicial 2 de 3</small>
      </v-stepper-step>
      <v-stepper-content step="2">
        <Form6 />
        <v-btn color="primary" @click="step = 3"> Continuar </v-btn>
        <v-btn text @click="ste
        p = 1"> Voltar </v-btn>

      </v-stepper-content>
        <v-stepper-step :complete="step > 3" step="3">
        Formulário do Dispositivo <small>Inicial 3 de 3</small>
      </v-stepper-step>
      <v-stepper-content step="3">
        <Form7 />
        <v-btn color="primary" @click="step = 4"> Continuar </v-btn>
        <v-btn text @click="step = 2"> Voltar </v-btn>
      </v-stepper-content>

    </v-stepper>
  </div>
</template>

<script>
import Form5 from "./Form5";
import Form6 from "./Form6";
import Form7 from "./Form7";

export default {
  components: {
    Form5,
    Form6,
    Form7
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