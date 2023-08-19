<script>
import mainScreen from "./components/mainScreen.vue";
import interact from "./components/interactScreen.vue";
import InteractScreen from './components/interactScreen.vue';
import { shuffled } from './utils/array.js';
export default {
  name: "App",
  data(){
    return {
      settings:{
        totalOfBlocks: 0,
        cardsContext: [],
        startedAt: null
      },
      statusMatch: "default",
    }
  },
  components: {
    mainScreen,
    InteractScreen
  },
  methods: {
    onHandleBeforeStart(configs){
      console.log("running handle before start, ", configs);
      this.settings.totalOfBlocks = configs.totalOfBlocks;
      const firstCards = Array.from(
        { length: this.settings.totalOfBlocks / 2 },
        (_, i) => i + 1
      ); 
      const secondCards = [...firstCards];
      const cards = [...firstCards, ...secondCards]
      console.log(cards);
      this.settings.cardsContext = shuffled(shuffled(shuffled(shuffled(cards))));
      this.settings.startedAt = new Date().getTime();
      // data ready
      this.statusMatch = "match";
    }
  }
}
</script>

<template>
  <main-screen v-if="statusMatch === 'default'" @onStart="onHandleBeforeStart($event)"/>
  <interact-screen v-if="statusMatch === 'match'" :cardsContext="cardsContext"/>
</template>

<style>
</style>
