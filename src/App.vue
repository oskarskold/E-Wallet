<template>
  <div id="app">
    <Home
      v-if="showWallet"
      @switch="showWallet = false"
      :listOfCards="listOfCards"
      :active="activeCard"
      @active="activateCard"
    />
    <AddCard
      v-if="!showWallet"
      @switch="showWallet = true"
      @create-card="addNewCard($event)"
      :listOfCards="listOfCards"
    />
  </div>
</template>

<script>
import Home from "./views/Home.vue";
import AddCard from "./views/AddCard.vue";

export default {
  name: "App",
  components: {
    Home,
    AddCard,
  },
  data() {
    return {
      showWallet: true,
      listOfCards: [],
      activeCard: {},
    };
  },
  methods: {
    addNewCard(theNewCard) {
      this.listOfCards.push(theNewCard);
    },
    activateCard(card) {
      this.activeCard = card;
    },
  },
};
</script>

<style scoped lang="scss">
@import url("https://fonts.googleapis.com/css2?family=PT+Mono&family=Source+Sans+Pro&display=swap");
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
h1 {
  font-family: "Source Sans Pro", sans-serif;
}
p {
  font-family: "PT Mono", monospace;
}
div {
  display: flex;
  align-items: center;
  flex-direction: column;
}
nav {
  margin: 1rem;
}
a {
  margin: 0.5rem;
}
</style>
