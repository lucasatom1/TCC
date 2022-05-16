<template>
    <v-checkbox :label="number + '. ' + text"></v-checkbox>
</template>

<script>
export default {
  name: "QuestionType2",
  props: {
    text: String,
    number: Number,
  },
};
</script>

<style lang="scss" scoped>
</style>