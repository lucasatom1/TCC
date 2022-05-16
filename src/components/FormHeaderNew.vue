<template>
  <v-container class="mb-2">
    <v-row class="justify-center text-center">
      <v-col
        cols="12"
        sm="12"
        lg="2"
        class="bordercard pt-8"
        :style="{ 'background-color': boxColor }"
      >
        <p class="font-weight-bold">{{ textLeft1 }}</p>
        <p>{{ textLeft2 }}</p>
      </v-col>
      <v-col cols="12" sm="12" lg="8">
        <h2 class="font-weight-black">
          {{ textMiddle1 }}
        </h2>
        <h2 class="font-weight-black">{{ textMiddle2 }}</h2>
        <p>{{ textMiddle3 }}</p>
      </v-col>
      <v-col
        cols="12"
        sm="12"
        lg="2"
        class="bordercard pt-8"
        :style="{ 'background-color': boxColor }"
      >
        <p>{{ textRight1 }}</p>
        <p class="font-weight-bold">{{ textRight2 }}</p>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "FormHeader",
  props: {
    textLeft1: {
      type: String,
    },
    textLeft2: {
      type: String,
    },
    textMiddle1: {
      type: String,
    },
    textMiddle2: {
      type: String,
    },
    textMiddle3: {
      type: String,
    },
    textRight1: {
      type: String,
    },
    textRight2: {
      type: String,
    },
    boxColor: {
      type: String,
    },
  },
};
</script>

<style lang="scss">
.bordercard {
  border: 1px solid black;
}
</style>