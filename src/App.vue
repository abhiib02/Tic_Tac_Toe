<template>
  <div id="app">
    <div class="turn Vuewer">
      <h1>Turn Vuewer</h1>
      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
      <h1 v-if="activePlayer" class="isCross">Red Turn</h1>
      <h1 v-else class="isRing">Blue Turn</h1>
    </div>
    <div class="center">
      <div class="grid">
        <div
          @click="changeActivePlayer(1)"
          v-bind:class="[
            { disabled: one },
            { isRing: one_R },
            { isCross: one_C },
            'one',
          ]"
        >
          1
        </div>
        <div
          @click="changeActivePlayer(2)"
          v-bind:class="[
            { disabled: two },
            { isRing: two_R },
            { isCross: two_C },
            'two',
          ]"
        >
          2
        </div>
        <div
          @click="changeActivePlayer(3)"
          v-bind:class="[
            { disabled: three },
            { isRing: three_R },
            { isCross: three_C },
            'three',
          ]"
        >
          3
        </div>
        <div
          @click="changeActivePlayer(4)"
          v-bind:class="[
            { disabled: four },
            { isRing: four_R },
            { isCross: four_C },
            'four',
          ]"
        >
          4
        </div>
        <div
          @click="changeActivePlayer(5)"
          v-bind:class="[
            { disabled: five },
            { isRing: five_R },
            { isCross: five_C },
            'five',
          ]"
        >
          5
        </div>
        <div
          @click="changeActivePlayer(6)"
          v-bind:class="[
            { disabled: six },
            { isRing: six_R },
            { isCross: six_C },
            'six',
          ]"
        >
          6
        </div>
        <div
          @click="changeActivePlayer(7)"
          v-bind:class="[
            { disabled: seven },
            { isRing: seven_R },
            { isCross: seven_C },
            'seven',
          ]"
        >
          7
        </div>
        <div
          @click="changeActivePlayer(8)"
          v-bind:class="[
            { disabled: eight },
            { isRing: eight_R },
            { isCross: eight_C },
            'eigth',
          ]"
        >
          8
        </div>
        <div
          @click="changeActivePlayer(9)"
          v-bind:class="[
            { disabled: nine },
            { isRing: nine_R },
            { isCross: nine_C },
            'nine',
          ]"
        >
          9
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      one: 0,
      two: 0,
      three: 0,
      four: 0,
      five: 0,
      six: 0,
      seven: 0,
      eight: 0,
      nine: 0,
      one_R: false,
      two_R: false,
      three_R: false,
      four_R: false,
      five_R: false,
      six_R: false,
      seven_R: false,
      eight_R: false,
      nine_R: false,
      one_C: false,
      two_C: false,
      three_C: false,
      four_C: false,
      five_C: false,
      six_C: false,
      seven_C: false,
      eight_C: false,
      nine_C: false,
      winningCombination: [123, 456, 789, 147, 258, 369, 159, 357],
      activePlayer: false, //0 is ring and 1 is cross
      posPressed: "",
    };
  },
  methods: {
    changeActivePlayer(pos) {
      ////////////////////////////////////////////////////////////////
      this.toggleClassAndSetButtonState(pos);

      this.activePlayer = !this.activePlayer;
      // winning logic
      if (
        (this.one !== 0 &&
          this.one === 1 &&
          this.one === this.two &&
          this.two === this.three) ||
        (this.four !== 0 &&
          this.four === 1 &&
          this.four === this.five &&
          this.five === this.six) ||
        (this.seven !== 0 &&
          this.seven === 1 &&
          this.seven === this.eight &&
          this.eight === this.nine) ||
        (this.one !== 0 &&
          this.one === 1 &&
          this.one === this.four &&
          this.four === this.seven) ||
        (this.two !== 0 &&
          this.two === 1 &&
          this.two === this.five &&
          this.five === this.eight) ||
        (this.three !== 0 &&
          this.three === 1 &&
          this.three === this.six &&
          this.six === this.nine) ||
        (this.one !== 0 &&
          this.one === 1 &&
          this.one === this.five &&
          this.five === this.nine) ||
        (this.three !== 0 &&
          this.three === 1 &&
          this.three === this.five &&
          this.five === this.seven)
      ) {
        alert("Blue Wins");
        this.resetData();
      }
      if (
        (this.one !== 0 &&
          this.one === 2 &&
          this.one === this.two &&
          this.two === this.three) ||
        (this.four !== 0 &&
          this.four === 2 &&
          this.four === this.five &&
          this.five === this.six) ||
        (this.seven !== 0 &&
          this.seven === 2 &&
          this.seven === this.eight &&
          this.eight === this.nine) ||
        (this.one !== 0 &&
          this.one === 2 &&
          this.one === this.four &&
          this.four === this.seven) ||
        (this.two !== 0 &&
          this.two === 2 &&
          this.two === this.five &&
          this.five === this.eight) ||
        (this.three !== 0 &&
          this.three === 2 &&
          this.three === this.six &&
          this.six === this.nine) ||
        (this.one !== 0 &&
          this.one === 2 &&
          this.one === this.five &&
          this.five === this.nine) ||
        (this.three !== 0 &&
          this.three === 2 &&
          this.three === this.five &&
          this.five === this.seven)
      ) {
        alert("Red Wins");
        this.resetData();
      }
      if (
        this.one !== 0 &&
        this.two !== 0 &&
        this.three !== 0 &&
        this.four !== 0 &&
        this.five !== 0 &&
        this.six !== 0 &&
        this.seven !== 0 &&
        this.eight !== 0 &&
        this.nine !== 0
      ) {
        alert("Match draw");
        this.resetData();
      }
    },
    resetData() {
      this.one = 0;
      this.two = 0;
      this.three = 0;
      this.four = 0;
      this.five = 0;
      this.six = 0;
      this.seven = 0;
      this.eight = 0;
      this.nine = 0;
      this.one_R = false;
      this.two_R = false;
      this.three_R = false;
      this.four_R = false;
      this.five_R = false;
      this.six_R = false;
      this.seven_R = false;
      this.eight_R = false;
      this.nine_R = false;
      this.one_C = false;
      this.two_C = false;
      this.three_C = false;
      this.four_C = false;
      this.five_C = false;
      this.six_C = false;
      this.seven_C = false;
      this.eight_C = false;
      this.nine_C = false;
      this.activePlayer = false; //0 is ring and 1 is cross
      this.posPressed = "";
    },
    toggleClassAndSetButtonState(temp) {
      switch (temp) {
        case 1:
          this.one = this.activePlayer ? 2 : 1;
          if (this.activePlayer) {
            this.one_C = !this.one_C;
          } else {
            this.one_R = !this.one_R;
          }
          break;
        case 2:
          this.two = this.activePlayer ? 2 : 1;
          if (this.activePlayer) {
            this.two_C = !this.two_C;
          } else {
            this.two_R = !this.two_R;
          }
          break;
        case 3:
          this.three = this.activePlayer ? 2 : 1;
          if (this.activePlayer) {
            this.three_C = !this.three_C;
          } else {
            this.three_R = !this.three_R;
          }
          break;
        case 4:
          this.four = this.activePlayer ? 2 : 1;
          if (this.activePlayer) {
            this.four_C = !this.four_C;
          } else {
            this.four_R = !this.four_R;
          }
          break;
        case 5:
          this.five = this.activePlayer ? 2 : 1;
          if (this.activePlayer) {
            this.five_C = !this.five_C;
          } else {
            this.five_R = !this.five_R;
          }
          break;
        case 6:
          this.six = this.activePlayer ? 2 : 1;
          if (this.activePlayer) {
            this.six_C = !this.six_C;
          } else {
            this.six_R = !this.six_R;
          }
          break;
        case 7:
          this.seven = this.activePlayer ? 2 : 1;
          if (this.activePlayer) {
            this.seven_C = !this.seven_C;
          } else {
            this.seven_R = !this.seven_R;
          }
          break;
        case 8:
          this.eight = this.activePlayer ? 2 : 1;
          if (this.activePlayer) {
            this.eight_C = !this.eight_C;
          } else {
            this.eight_R = !this.eight_R;
          }
          break;
        case 9:
          this.nine = this.activePlayer ? 2 : 1;
          if (this.activePlayer) {
            this.nine_C = !this.nine_C;
          } else {
            this.nine_R = !this.nine_R;
          }
          break;
        default:
      }
    },
  },
};
</script>

<style>
html {
  overflow: hidden;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  transform: scale(0.5);
}
.one {
  grid-area: one;
}
.two {
  grid-area: two;
}
.three {
  grid-area: three;
}
.four {
  grid-area: four;
}
.five {
  grid-area: five;
}
.six {
  grid-area: six;
}
.seven {
  grid-area: seven;
}
.eight {
  grid-area: eight;
}
.nine {
  grid-area: nine;
}

.grid {
  display: grid;
  grid-gap: 10px;
  width: 200px;
  transform: translate(-100%);
  grid-template-areas:
    "one two three"
    "four five six"
    "seven eight nine";
}
.grid > div {
  width: 200px;
  height: 200px;
  display: grid;
  place-items: center;
  font-size: 5rem;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.24), 0 1px 2px rgba(0, 0, 0, 0.48);
  transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
}
.grid > div:hover {
  box-shadow: 0 14px 28px rgba(0, 0, 0, 0.25), 0 10px 10px rgba(0, 0, 0, 0.22);
}
.center {
  display: flex;
  align-items: center;
  justify-content: center;
}
.disabled {
  pointer-events: none;
  background: #333;
}
.isRing {
  background: hsl(204, 86%, 53%);
}
.isCross {
  background: hsl(348, 100%, 61%);
}
.Vuewer {
  display: flex;
  justify-content: center;
  flex-direction: row;
}
</style>
