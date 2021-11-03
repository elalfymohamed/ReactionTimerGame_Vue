<template>
  <div
    class="block"
    :style="{
      position: 'absolute',
      top: y + 'px',
      left: x + 'px',
    }"
    v-if="showBlock"
    @click="stopTimer"
  >
    click me
  </div>
</template>

<script>
export default {
  name: "Block",
  props: {
    delay: Number,
    x: Number,
    y: Number,
  },
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    };
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit("end", this.reactionTime);
    },
  },
};
</script>

<style scoped>
.block {
  width: 250px;
  border-radius: 20px;
  background-color: #0faf87;
  color: #fff;
  text-align: center;
  padding: 80px 0;
  margin: 40px auto;
}
</style>
