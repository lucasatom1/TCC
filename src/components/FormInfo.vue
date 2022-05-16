<template>
  <v-container :style="{ 'background-color': boxColor }">
    <v-form>
      <v-row>
        <v-col cols="12" sm="6" md="8" v-if="name">
          <v-text-field dense :label="name"></v-text-field>
        </v-col>

        <v-col cols="12" sm="6" md="4" v-if="age">
          <v-text-field dense :label="age"></v-text-field>
        </v-col>
      </v-row>

      <v-row>
        <v-col cols="12" sm="6" md="8" v-if="shortGoals">
          <v-text-field
            dense
            :label="shortGoals"
          ></v-text-field>
        </v-col>
        <v-col cols="12" sm="6" md="4" v-if="date">
          <v-text-field dense :label="date"></v-text-field>
        </v-col>
      </v-row>

      <v-row>
        <v-col cols="12" sm="6" md="8" v-if="longGoals">
          <v-text-field
            dense
            :label="longGoals"
          ></v-text-field>
        </v-col>
        <v-col cols="12" sm="6" md="4" v-if="appraiser">
          <v-text-field dense :label="appraiser"></v-text-field>
        </v-col>
      </v-row>
    </v-form>
  </v-container>
</template>

<script>
export default {
  name: "FormInfo",

  props: {
    name: {
      type: String,
    },
    shortGoals: {
      type: String,
    },
    longGoals: {
      type: String,
    },
    age: {
      type: String,
    },
    appraiser: {
      type: String,
    },
    date: {
      type: String,
    },
    boxColor: {
      type: String,
    },
  },
};
</script>

<style lang="scss" scoped>
</style>