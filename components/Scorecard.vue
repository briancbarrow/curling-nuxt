<template>
  <div>
    <h1>Testing</h1>
    <table>
      <tbody>
        <tr>
          <th>Players</th>
          <th v-for="index in ends" :key="index">{{index}}</th>
          <th>Total</th>
        </tr>
        <tr>
          <td class="playerName">Player 1</td>
          <td v-for="index in ends" :key="index">
            <input class="scoreInput1" type="number" v-on:keyup="totalScore">
          </td>
          <td>{{ total.player1 }}</td>
        </tr>
        <tr>
          <td class="playerName">Player 2</td>
          <td v-for="index in ends" :key="index">
            <input class="scoreInput2" type="number" v-on:keyup="totalScore">
          </td>
          <td>{{ total.player2 }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      ends: 10,
      total: {
        player1: 0,
        player2: 0
      }
    }
  },
  methods: {
    totalScore() {
      const player1Inputs = document.getElementsByClassName('scoreInput1')
      const player2Inputs = document.getElementsByClassName('scoreInput2')
      this.total.player1 = 0
      this.total.player2 = 0

      for (let i = 0; i < player1Inputs.length; i++) {
        const inputValue = parseInt(player1Inputs[i].value)
        if (inputValue) {
          this.total.player1 += parseInt(player1Inputs[i].value)
        }
      }
      for (let i = 0; i < player2Inputs.length; i++) {
        const inputValue = parseInt(player2Inputs[i].value)
        if (inputValue) {
          this.total.player2 += parseInt(player2Inputs[i].value)
        }
      }
    }
  }
}
</script>

<style scoped>
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  /* display: none; <- Crashes Chrome on hover */
  -webkit-appearance: none;
  margin: 0; /* <-- Apparently some margin are still there even though it's hidden */
}

input[type='number'] {
  -moz-appearance: textfield; /* Firefox */
}

input {
  max-width: 40px;
  height: 40px;
  text-align: center;
  font-size: 0.9rem;
}
</style>
