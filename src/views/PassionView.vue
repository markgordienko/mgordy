<template>
  <div class="passion">
    <transition appear name="fade">
      <div
        @click="success = !success"
        class="success container-s"
        v-if="success"
      >
        <img
          class="heart"
          src="@/assets/free-heart-icon-3510-thumb.png"
          alt=""
        />
      </div>
    </transition>

    <div v-show="!success">
      <div class="header">
        <h1>Здравствуй, моя пассия</h1>

        <h3>Запомнила загаданное число? Используй его в загадке.</h3>

        <h5>Подсказка: каждой букве алфавита соответсвует какая-то другая</h5>

        <input
          v-model="message"
          placeholder="Введи сообщение"
          class="text-input"
        />
      </div>

      <div>
        <div class="list">
          <span v-for="item in items" :key="item"
            ><PassionLettersComponent :letter="item" @test="writeInd"
          /></span>
        </div>
      </div>

      <button @click="test" class="check-btn">ПРОВЕРИТЬ</button>
    </div>

    <br />
    <div class="decrypted">
      <span> {{ decryptedMessage }}</span>
    </div>
  </div>
</template>

<script>
import PassionLettersComponent from "./PassionLettersComponent.vue";

export default {
  components: {
    PassionLettersComponent,
  },
  data() {
    return {
      message: "",
      items: [
        "a",
        "b",
        "c",
        "d",
        "e",
        "f",
        "g",
        "h",
        "i",
        "j",
        "k",
        "l",
        "m",
        "n",
        "o",
        "p",
        "q",
        "r",
        "s",
        "t",
        "u",
        "v",
        "w",
        "x",
        "y",
        "z",
      ],
      newItems: [
        "a",
        "b",
        "c",
        "d",
        "e",
        "f",
        "g",
        "h",
        "i",
        "j",
        "k",
        "l",
        "m",
        "n",
        "o",
        "p",
        "q",
        "r",
        "s",
        "t",
        "u",
        "v",
        "w",
        "x",
        "y",
        "z",
      ],
      temp: [
        "a",
        "b",
        "c",
        "d",
        "e",
        "f",
        "g",
        "h",
        "i",
        "j",
        "k",
        "l",
        "m",
        "n",
        "o",
        "p",
        "q",
        "r",
        "s",
        "t",
        "u",
        "v",
        "w",
        "x",
        "y",
        "z",
      ],
      decryptedMessage: "",
      tempStr: "",
      success: true,
    };
  },
  watch: {
    message(newVal) {
      this.tempStr = newVal;
      this.decryptedMessage = newVal;
    },
  },
  mounted() {
    console.log(9);
  },
  methods: {
    setCharAt(str, index, chr) {
      if (index > str.length - 1) return str;
      return str.substring(0, index) + chr + str.substring(index + 1);
    },
    test() {
      this.temp = this.items;
      let tempStr = this.decryptedMessage.split("");
      for (let i = 0; i < this.decryptedMessage.length; i++) {
        let currLet = this.tempStr[i];
        let currLetInd = this.items.indexOf(currLet);

        if (this.tempStr[i].toLowerCase() != this.tempStr[i].toUpperCase()) {
          // tempStr.splice(6, 1, this.newItems[currLetInd]);
          tempStr[i] = this.newItems[currLetInd];
        }
      }
      console.log(tempStr);
      this.decryptedMessage = tempStr.join("");
    },
    writeInd(q) {
      this.newItems[this.items.indexOf(q[0])] = q[1];
    },
  },
};
</script>

<style>
.passion {
  position: relative;
}
.header {
  z-index: 10;
}
.list-container {
  display: block;
  text-align: center;
  position: absolute;
}
.list {
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
}
.check-btn {
  background-color: #2e615e;
  border-radius: 8px;
  border-style: none;
  color: #ffffff;
  margin-top: 40px;
  height: 60px;
  width: 150px;
  text-align: center;
  text-decoration: none;
  transition: color 100ms;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
  font-size: 20px;
  font-family: Avenir, Helvetica, Arial, sans-serif;
}

.check-btn:hover {
  background-color: #457775;
}

.success {
  background: linear-gradient(-45deg, #ee7752, #8e4fc2, #23a6d5, #23d5ab);
  background-size: 400% 400%;
  animation: gradient 10s infinite;
  border-radius: 400px;
  width: 800px;
  height: 800px;

  display: flex;
  justify-content: center;
  align-items: center;
}

.container-s {
  position: absolute;
  text-align: center;
  left: 30%;
  z-index: -1;
}

@keyframes gradient {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
.text-input {
  width: 30%;
  border-radius: 5px;
  padding: 20px 40px;
  margin: 0;
  font-size: 20px;
}
.decrypted {
  margin-top: 15px;
  font-size: 30px;
  font-weight: 300;
}
</style>
