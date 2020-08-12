<template>
  <div id="app">
    <div class="simon">
      <h1>{{title}}</h1>
      <div class="simon__row">
        <div class="simon__buttons">
          <button
            :class="{light: light[1]}"
            :disabled="!userTurn"
            class="btnGreen"
            @click="clickedBtn(1)"
          ></button>
          <button
            :class="{light: light[2]}"
            :disabled="!userTurn"
            class="btnYellow"
            @click="clickedBtn(2)"
          ></button>
          <button
            :class="{light: light[3]}"
            :disabled="!userTurn"
            class="btnRed"
            @click="clickedBtn(3)"
          ></button>
          <button
            :class="{light: light[4]}"
            :disabled="!userTurn"
            class="btnBlue"
            @click="clickedBtn(4)"
          ></button>
        </div>
        <div class="simon__menu">
          <h2 class="round">Round: {{round}}</h2>

          <button @click="start">{{startBtn}}</button>
          <h2>Level:</h2>
          <ul>
            <li v-for="(lvl,index) in levels" :key="index">
              <input name="level" :value="index" :id="index" type="radio" v-model="lvlPicked" />
              <label :for="lvl">{{index}}</label>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
var timer;
export default {
  data() {
    return {
      round: 0,
      startBtn: "Start",
      title: "Simon The Game",
      userTurn: false,
      light: {
        1: false,
        2: false,
        3: false,
        4: false,
      },
      index: 0,
      sequence: [],
      lvlPicked: "Eazy",
      levels: {
        Eazy: 1500,
        Medium: 1000,
        Hard: 500,
      },
    };
  },
  computed: {
    delay() {
      let delay = "";
      switch (this.lvlPicked) {
        case "Eazy":
          delay = this.levels.Eazy;
          break;
        case "Medium":
          delay = this.levels.Medium;
          break;
        default:
          delay = this.levels.Hard;
      }
      return delay;
    },
  },
  methods: {
    start() {
      if (this.startBtn === "Start") {
        this.startBtn = "Stop";
        this.simonTurn();
      } else {
        this.reset();
      }
    },
    simonTurn() {
      this.index = 0;
      this.round++;
      this.sequence.push(this.randomNumber());
      this.showSequence(() => {
        this.userTurn = true;
      });
    },
    showSequence(callback) {
      var self = this;
      var i = 0;
      timer = setInterval(function () {
        if (i >= self.sequence.length) {
          self.stopInterval();
        }
        self.animate(self.sequence[i]);
        i++;
      }, this.delay);
      callback();
    },
    stopInterval: function () {
      clearInterval(timer);
    },
    randomNumber() {
      return Math.floor(Math.random() * 4 + 1);
    },
    reset() {
      this.startBtn = "Start";
      this.sequence = [];
      this.userTurn = false;
      this.round = 0;
      this.index = 0;
    },
    clickedBtn(num) {
      this.animate(num);
      if (!this.isSequenceCorrect(num)) {
        this.gameOver();
        return;
      } else {
        if (this.index === this.sequence.length - 1) {
          setTimeout(() => {
            this.userTurn = false;
            this.simonTurn();
          }, 1000);
        } else {
          this.index++;
        }
      }
    },
    isSequenceCorrect(num) {
      return this.sequence[this.index] === num;
    },
    animate(num) {
      this.light[num] = true;
      let audio = new Audio(require("./assets/sounds/" + num + ".mp3"));
      audio.play();
      // Можно использовать self для переопределения this, но и так читаемость нормальная
      setTimeout(() => {
        this.light[num] = false;
      }, 500);
      return;
    },
    gameOver() {
      this.title = "Game over!";
      this.reset();
    },
  },
};
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  justify-content: center;
}

.simon {
  &__row {
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 50px;
    .simon__buttons {
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      justify-content: center;
      width: 400px;
      button {
        height: 150px;
        width: 150px;
        border: none;
        outline: none;
        opacity: 0.6;
      }
      button.light {
        opacity: 1;
      } 
    }
  }
  &__menu {
    display: flex;
    flex-direction: column;
    padding: 30px;
    h2 {
      margin-bottom: 10px;
    }
    button {
      margin-bottom: 20px;
    }
    ul {
      display: flex;
      flex-direction: column;
      align-items: flex-start;
      justify-content: flex-start;
      list-style: none;
      padding: 3px;
      li {
        padding: 2px;
        label {
          margin-left: 10px;
        }
      }
    }
  }
}

.btnGreen {
  background-color: dodgerblue;
  border-top-left-radius: 100%;
}
.btnYellow {
  background-color: #ff5643;
  border-top-right-radius: 100%;
}
.btnRed {
  background-color: #feef33;
  border-bottom-left-radius: 100%;
}
.btnBlue {
  background-color: #bede15;
  border-bottom-right-radius: 100%;
}
</style>
