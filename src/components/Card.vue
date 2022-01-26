<template>
  <div @click="$emit('active', card)" class="create-card">
    <div class="card" :class="[card.vendor]">
      <div class="card-header">
        <div class="card-header-left">
          <img src="../assets/wifi_white.svg" alt="wifi icon" />
          <img src="../assets/chip.svg" alt="chip icon" />
        </div>
        <div class="card-header-right">
          <img :src="iconPath" alt="icon" />
        </div>
      </div>
      <div class="card-middle">
        <p>{{ spacecardNumber }}</p>
      </div>
      <div class="card-footer">
        <div class="card-footer-left">
          <p>CARDHOLDER NAME</p>
          <p>{{ card.cardHolder }}</p>
        </div>
        <div class="card-footer-right">
          <p>VALID THRU</p>
          <p>
            {{ card.expireMonth }} /
            {{ card.expireYear }}
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: { card: Object },
  methods: {},
  data() {
    return {};
  },
  computed: {
    iconPath() {
      return require(`../assets/${this.card.vendor}.svg`);
    },
    spacecardNumber() {
      return (
        this.card.cardNumber.slice(0, 4) +
        " " +
        this.card.cardNumber.slice(4, 8) +
        " " +
        this.card.cardNumber.slice(8, 12) +
        " " +
        this.card.cardNumber.slice(12, 16)
      );
    },
  },
};
</script>

<style scoped lang="scss">
@import url("https://fonts.googleapis.com/css2?family=PT+Mono&family=Source+Sans+Pro&display=swap");
.card {
  background: #f33355;
  border-radius: 1rem;
  margin: 1rem;
  padding: 1.4rem;
  color: whitesmoke;
  font-family: "PT Mono", monospace;
  max-width: 420px;
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
