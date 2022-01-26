<template>
  <div>
    <Card
      v-for="card in listOfCards"
      :key="card.id"
      :card="card"
      @active="$emit('active', card)"
    />
  </div>
</template>

<script>
import Card from "./Card.vue";
export default {
  components: { Card },
  props: { listOfCards: Array, active: Array },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=PT+Mono&family=Source+Sans+Pro&display=swap");
.card {
  background: #f33355;
  border-radius: 1rem;
  margin: 1rem;
  padding: 1.4rem;
  color: whitesmoke;
  font-family: "PT Mono", monospace;
}
.bitcoin {
  background-color: #ffae34;
}
.blockchain {
  background-color: #8b58f9;
}
.evil {
  background-color: #f33355;
}
.ninja {
  background-color: #222222;
  color: white;
}
.card-header {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  width: 400px;
  margin-bottom: 1rem;
}

.card-header-left {
  display: flex;
  flex-direction: column;
}
.card-header-right {
  display: flex;
  flex-direction: column;
}
.card-middle {
  display: flex;
  flex-direction: column;
  align-self: center;
}
.card-middle > p {
  font-size: 2.2rem;
}
.card-footer {
  display: flex;
}
.card-footer-left {
  margin: 1rem 5rem 0 0;
}
.card-footer-right {
  margin: 1rem 0 0 5rem;
}
</style>
