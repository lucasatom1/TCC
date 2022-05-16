<template>
  <div>
    <v-tabs v-model="tab" background-color="transparent" color="basil" grow>
      <v-tab key="Exemplo"> ATP PA </v-tab>
      <v-tab key="form12"> Form 1-2 </v-tab>
      <v-tab key="form34"> Form 3-4 </v-tab>
      <v-tab key="form567"> Form 5-6-7 </v-tab>
      <v-tab key="form89"> Form 8-9 </v-tab>
    </v-tabs>

    <v-tabs-items v-model="tab">
      <v-tab-item key="Exemplo">
        <v-card color="basil" flat>
          <Form3 />
        </v-card>
      </v-tab-item>

      <v-tab-item key="form12">
        <v-card color="basil" flat>
          <FormPage1 />
        </v-card>
      </v-tab-item>

      <v-tab-item key="form34">
        <v-card color="basil" flat>
          <Form6 />
        </v-card>
      </v-tab-item>

      <v-tab-item key="form567">
        <v-card color="basil" flat>
          <FormPage5 />
        </v-card>
      </v-tab-item>

      <v-tab-item key="form89">
        <v-card color="basil" flat>
          <Form6 />
        </v-card>
      </v-tab-item>
    </v-tabs-items>
  </div>
</template>

<script>
import FormPage1 from "./FormPage1";
import FormPage5 from "./FormPage5";

import Form6 from "./Form6";
import Form7 from "./Form7";
import Form3 from "./Form3";

export default {
  components: {
    FormPage1,
    Form6,
    Form7,
    Form3,
    FormPage5
  },
  data() {
    return {
      tab: "form567",
    };
  },
};
</script>

<style lang="scss" scoped>
</style>