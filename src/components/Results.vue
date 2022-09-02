<template>
  <p>Reaction Time : {{ score }} ms</p>
</template>

<script>
export default {
  props: ["score"],
  name: "ResultsGame",
};
</script>

<style></style>
