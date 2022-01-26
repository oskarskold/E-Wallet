<template>
  <div>
    <h1>ADD A NEW BANK CARD</h1>
    <h5>NEW CARD</h5>
    <Card :card="cardMust" />
    <form @submit.prevent="submit">
      <label>CARD NUMBER</label>
      <input type="text" v-model="cardMust.cardNumber" maxlength="16" />
      <label>CARDHOLDER NAME</label>
      <input type="text" v-model="cardMust.cardHolder" maxlength="20" />

      <section class="expire">
        <div class="expire-date">
          <label>MONTH</label>
          <select v-model="cardMust.expireMonth">
            <option
              v-for="month in dateMonths"
              :key="month"
              :value="month"
              selected
            >
              {{ month }}
            </option>
          </select>
        </div>

        <div class="expire-date">
          <label>YEAR</label>
          <select v-model="cardMust.expireYear">
            <option
              v-for="year in dateYears"
              :key="year"
              :value="year.toString().substr(2)"
              selected
            >
              {{ year }}
            </option>
          </select>
        </div>
      </section>

      <label>VENDOR</label>
      <select v-model="cardMust.vendor">
        <option
          v-for="vendor in vendors"
          :key="vendor.value"
          :value="vendor.value"
        >
          {{ vendor.text }}
        </option>
      </select>
    </form>

    <button @click="switchAndEmitData">ADD CARD</button>
  </div>
</template>

<script>
import Card from "../components/Card.vue";

export default {
  data() {
    return {
      cardMust: {
        vendor: "bitcoin",
        cardNumber: "",
        cardHolder: "",
        expireMonth: "",
        expireYear: "",
      },
      vendors: [
        { text: "Bitcoin Inc", value: "bitcoin" },
        { text: "Evil Corp", value: "evil" },
        { text: "Ninja Bank", value: "ninja" },
        { text: "Blockchain Inc", value: "blockchain" },
      ],
      dateMonths: {
        1: "01",
        2: "02",
        3: "03",
        4: "04",
        5: "05",
        6: "06",
        7: "07",
        8: "08",
        9: "09",
        10: "10",
        11: "11",
        12: "12",
      },
      dateYears: {
        2022: "2022",
        2023: "2023",
        2024: "2024",
        2025: "2025",
        2026: "2026",
        2027: "2027",
      },
    };
  },
  props: ["showWallet"],
  components: { Card },
  methods: {
    switchAndEmitData() {
      this.$emit("create-card", this.cardMust);
      this.$emit("switch");
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
  background: black;
  color: white;
  border: none;
  font-family: "PT Mono", monospace;
  font-size: 1rem;
  font-weight: 700;
  border-radius: 1rem;
  margin-top: 7em;
}
button:hover {
  background: rgb(107, 106, 106);
  cursor: pointer;
}
form {
  display: flex;
  flex-direction: column;
  margin: 2rem;
}

label,
select,
option {
  margin: 1rem;
  font-family: "PT Mono", monospace;
  font-size: 1.5rem;
}
input,
select {
  padding: 1.5rem 2rem;
  margin: 0 1rem;
  font-size: 1.5rem;
}

.expire {
  display: flex;
  justify-content: space-evenly;
}
</style>
