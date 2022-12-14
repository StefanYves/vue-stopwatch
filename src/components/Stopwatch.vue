<template>
  <div>
    <p>{{ minutes }}:{{ seconds }}</p>
    <button @click="start">Start</button>
    <button @click="stop">Stop</button>
    <button @click="reset">Reset</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      minutes: 0,
      seconds: 0,
      interval: null,
    };
  },
  methods: {
    start() {
      if (this.interval) return;
      this.interval = setInterval(() => {
        this.seconds++;
        if (this.seconds >= 60) {
          this.seconds = 0;
          this.minutes++;
        }
      }, 1000);
    },
    stop() {
      clearInterval(this.interval);
      this.interval = null;
    },
    reset() {
      this.minutes = 0;
      this.seconds = 0;
    },
  },
};
</script>
