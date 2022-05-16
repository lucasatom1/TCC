<template>
  <v-container>
    <!--class="mediumPurple" -->
    <v-row class="align-center pa-n10">
      <v-col cols="12" sm="6" md="1">
        <h4>{{ id }}</h4>
      </v-col>

      <v-col cols="12" sm="6" md="4">
        <p>{{ text }}</p>
      </v-col>

      <v-col cols="12" sm="6" md="1">
        <p>{{ exampleNumber }}</p>
      </v-col>

      <v-col cols="12" sm="6" md="2">
        <v-text-field
          dense
          label=""
          type="number"
          v-model="device1"
          @change="$emit('device1', { value: parseInt(device1), id: id })"
        ></v-text-field>
      </v-col>

      <v-col cols="12" sm="6" md="2">
        <v-text-field
          dense
          label=""
          type="number"
          v-model="device2"
          @change="$emit('device2', { value: parseInt(device2), id: id })"
        ></v-text-field>
      </v-col>

      <v-col cols="12" sm="6" md="2">
        <v-text-field
          dense
          label=""
          type="number"
          v-model="device3"
          @change="$emit('device3', { value: parseInt(device3), id: id })"
        ></v-text-field>
      </v-col>
    </v-row>
    <!-- se finalcomment =! de "" mostrar essa parte -->
    <v-row v-if="finalComment && finalComment != ''">
      <v-col cols="12" md="5" class="font-weight-bold">Total</v-col>
      <v-col cols="12" md="1"  class="font-weight-bold">47</v-col>
      <v-col cols="12" md="2"  class="font-weight-bold">{{ sumDevice1 }}</v-col>
      <v-col cols="12" md="2"  class="font-weight-bold">{{ sumDevice2 }}</v-col>
      <v-col cols="12" md="2"  class="font-weight-bold">{{ sumDevice3 }}</v-col>
    </v-row>

    <v-row v-if="finalComment && finalComment != ''" class="">
      <v-col cols="12" sm="6" md="12">
        <p>{{ finalComment }}</p>
      </v-col>
    </v-row>

    <template v-if="finalInfo">
      <FormFinal />
    </template>
  </v-container>
</template>

<script>
import FormFinal from "../components/Form2Specific/FormFinal";
export default {
  name: "QuestionType3",
  components: {
    FormFinal,
  },
  data() {
    return {
      device1: null,
      device2: null,
      device3: null,
    };
  },
  props: {
    id: {
      type: String,
    },
    text: {
      type: String,
    },
    exampleNumber: {
      type: String,
    },
    finalComment: {
      type: String,
    },
    finalInfo: {
      type: Boolean,
    },
    sumDevice1: Number,
    sumDevice2: Number,
    sumDevice3: Number,
  },
  watch: {
    sumDevice1(to) {
      console.log(to);
    },
  },
};
</script>

<style lang="scss" scoped>
.mediumPurple {
  background-color: rgb(205, 192, 218);
}
</style>