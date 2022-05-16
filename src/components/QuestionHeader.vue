<template>
  <v-container class="rounded mb-5">
    <h3>{{ id }}. {{ text }}</h3>
    <ul v-if="infos">
      <li v-for="info in infos" :key="info">
        {{ info }}
      </li>
    </ul>
    {{text2}}<br>
    {{text3}}
  </v-container>
</template>

<script>
export default {
  name: "QuestionHeader",
  props: {
    id: String,
    text: String,
    infos: Array,
    text2: String,
    text3: String,
  },
};
</script>

<style lang="scss" scoped>
</style>