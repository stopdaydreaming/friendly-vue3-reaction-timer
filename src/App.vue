<template>
  <h1>Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">play</button>
  <BlockTimer :delay="delay" v-if="isPlaying"/>
</template>

<script>
import BlockTimer from './components/BlockTimer.vue';

export default {
  name: 'App',
  components: { BlockTimer },
  data(){
    return {
      isPlaying: false,
      delay: null
    }
  },
  methods: {
    start() {
      this.delay = setTimeout(() => {
        this.isPlaying = true;
      }, Math.random() * 5000 + 2000);
      this.isPlaying = true;
      console.log(this.delay);
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
</style>
