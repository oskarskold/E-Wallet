<template>
  <div>
    <h1>E-Wallet</h1>
    <h5>ACTIVE CARD</h5>
    <Card :card="active" />
    <article>
      <CardList :listOfCards="listOfCards" @active="submitCard" />
    </article>
    <button @click="$emit('switch')">ADD A NEW CARD</button>
  </div>
</template>

<script>
import Card from "../components/Card.vue";
import CardList from "../components/CardList.vue";
export default {
  data() {
    return {
      activeCardData: [],
    };
  },
  components: { CardList, Card },
  props: ["showWallet", "listOfCards", "active"],
  methods: {
    submitCard(card) {
      this.activeCardData = card;
      this.$emit("active", this.activeCardData);
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
  margin: 1rem;
  font-family: "Source Sans Pro", sans-serif;
}
h5 {
  font-family: "PT Mono", monospace;
  font-size: 0.8rem;
  margin-top: 2rem;
}
p {
  font-family: "PT Mono", monospace;
  font-size: 0.6rem;
  margin: 2rem;
}
div {
  display: flex;
  align-items: center;
  flex-direction: column;
}
button {
  padding: 3rem 9rem;
  background: rgb(255, 255, 255);
  color: rgb(0, 0, 0);
  border: 1px solid black;
  font-family: "PT Mono", monospace;
  font-size: 1rem;
  font-weight: 700;
  border-radius: 1rem;
  position: absolute;
  top: 1300px;
}
button:hover {
  background: rgb(107, 106, 106);
  cursor: pointer;
}
</style>
