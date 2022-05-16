<template>
  <v-container class="m-0 p-0">
    <v-row v-if="Object.keys(info).length !== 0">
      <v-col cols="12" offset-md="4" md="4" xs="12" class="text-center">
        <span class="mr-6 font-weight-black">{{ info.scale1 }}</span>
        <span class="mr-6 font-weight-black">{{ info.scale2 }}</span>
        <span class="mr-6 font-weight-black">{{ info.scale3 }}</span>
      </v-col>
      <v-col cols="12" md="2" xs="12">
        <span class="font-weight-black">{{ info.input1 }}</span>
      </v-col>
      <v-col cols="12" md="2" xs="12">
         <span class="font-weight-black">{{ info.input2 }}</span>
      </v-col>
    </v-row>

    <v-row
      class="align-center pb-0 mb-0"
      :style="{ 'background-color': color }"
    >
      <v-col cols="12" md="4" xs="12">{{ number }}. {{ text }}</v-col>
      <v-col cols="12" md="4" xs="12" class="d-flex justify-center">
        <v-radio-group row>
          <v-radio label="1"></v-radio>
          <v-radio label="2"></v-radio>
          <v-radio label="3"></v-radio>
          <v-radio label="4"></v-radio>
          <v-radio label="5"></v-radio>
        </v-radio-group>
      </v-col>
      <v-col cols="12" md="4" xs="12" class="d-inline-flex">
        <v-text-field class="pr-2"></v-text-field>
        <v-text-field></v-text-field>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "QuestionType1",
  props: {
    text: String,
    number: Number,
    color: String,
    info: Object,
  },
};
</script>

<style lang="scss" scoped>
</style>