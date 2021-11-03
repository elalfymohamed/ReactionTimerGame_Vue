<template>
  <p>Reaction time: - {{ score }} ms</p>
  <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
  name: "Results",
  props: {
    score: Number,
  },
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score < 250) {
      this.rank = "You are a ninja fingers";
    } else if (this.score < 450) {
      this.rank = "You are a rapid reflexes";
    } else if (this.score < 650) {
      this.rank = "You are a fast";
    } else {
      this.rank = "You are a snail pace...";
    }
  },
};
</script>

<style>
.rank {
  font-size: 1.3em;
  font-weight: bold;
  color: #0faf89;
}
</style>
