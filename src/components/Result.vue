<template>
  <div>
    <h1>Resulat</h1>
    <p>Votre score est de {{ score }} ms</p>
  </div>
</template>

<script>
export default {
  name: "ResultZone",
  props: {
    score: Number,
  },
};
</script>

<style></style>
