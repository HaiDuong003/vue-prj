<script>
import CardFlip from "./card.vue";
export default {
  props:{
    cardsContext:{
      type: Array,
      default: function(){
        return [];
      }
    }
  },
  components: {
    CardFlip,
  }
}
</script>

<template>
  <h1>Interact Component here...</h1>
  <card-flip v-for="(card, index) in cardsContext" : key="index"/>
</template>