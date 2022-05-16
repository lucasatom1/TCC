<template>
  <v-container>
    <!--class="mediumPurple" -->
    <v-row v-if="infos">
      <v-col cols="1" offset="5" md="1">{{ infos.scale1 }}</v-col>
      <v-col cols="1" md="1">{{ infos.scale2 }}</v-col>
      <v-col cols="1" md="1">{{ infos.scale3 }}</v-col>
      <v-col cols="1" md="1">{{ infos.scale4 }}</v-col>
      <v-col cols="1" md="1">{{ infos.scale5 }}</v-col>
      <v-col cols="1" md="1">{{ infos.scale6 }}</v-col>
      <v-col cols="1" md="1">{{ infos.scale7 }}</v-col>
    </v-row>
    <v-row class="align-center pa-n10">
      <v-col cols="12" sm="6" md="1">
        <h4>{{ id }}</h4>
      </v-col>

      <v-col cols="12" sm="6" md="4">
        <p>{{ text }}</p>
      </v-col>

      <v-col cols="7" md="7">
        <v-radio-group
          v-model="radio"
          @change="$emit('scale', { value: parseInt(radio), id: id })"
          class="text-center"
        >
          <div class="d-flex">
            <div style="width: 14.28%">
              <v-radio></v-radio>
            </div>

            <div style="width: 14.28%">
              <v-radio></v-radio>
            </div>

            <div style="width: 14.28%">
              <v-radio></v-radio>
            </div>

            <div style="width: 14.28%">
              <v-radio></v-radio>
            </div>

            <div style="width: 14.28%">
              <v-radio></v-radio>
            </div>

            <div style="width: 14.28%">
              <v-radio></v-radio>
            </div>

            <div style="width: 14.28%">
              <v-radio></v-radio>
            </div>
          </div>
        </v-radio-group>
      </v-col>
    </v-row>
    <!-- se finalcomment =! de "" mostrar essa parte -->
    <v-row v-if="radioSum">
      <v-col cols="5" md="5" class="font-weight-bold">Total</v-col>
      <v-col cols="12" md="1" class="font-weight-bold">{{
        radioSum && radioSum[0] ? radioSum[0].length : 0
      }}</v-col>
      <v-col cols="12" md="1" class="font-weight-bold">{{
        radioSum && radioSum[1] ? radioSum[1].length : 0
      }}</v-col>
      <v-col cols="12" md="1" class="font-weight-bold">{{
        radioSum && radioSum[2] ? radioSum[2].length : 0
      }}</v-col>
      <v-col cols="12" md="1" class="font-weight-bold">{{
        radioSum && radioSum[3] ? radioSum[3].length : 0
      }}</v-col>
      <v-col cols="12" md="1" class="font-weight-bold">{{
        radioSum && radioSum[4] ? radioSum[4].length : 0
      }}</v-col>
      <v-col cols="12" md="1" class="font-weight-bold">{{
        radioSum && radioSum[5] ? radioSum[5].length : 0
      }}</v-col>
      <v-col cols="12" md="1" class="font-weight-bold">{{
        radioSum && radioSum[6] ? radioSum[6].length : 0
      }}</v-col>
    </v-row>
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
      radio: null,
    };
  },
  props: {
    id: {
      type: String,
    },
    text: {
      type: String,
    },
    finalSum: Boolean,
    infos: Object,
    radioSum: Object,
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