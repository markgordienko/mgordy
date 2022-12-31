<template>
  <div class="passion">
    <h3 class="letters">{{ letter }}</h3>

    <div class="selector">
      <button class="select-btn" @click="letterUp">▲</button>
      <div class="selected-letter">
        {{ selectedLetter }}
      </div>
      <button class="select-btn" @click="letterDown">▼</button>
    </div>
  </div>
</template>

<script>
export default {
  props: ["letter"],
  data() {
    return {
      message: "",
      selectedLetter: this.letter,
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
      currentLetterIndex: null,
      myLetter: this.letter,
    };
  },
  mounted() {
    this.currentLetterIndex = this.items.indexOf(this.letter);
  },
  methods: {
    init() {},
    letterUp() {
      this.currentLetterIndex++;
      this.currentLetterIndex %= 26;
      this.selectedLetter = this.items[this.currentLetterIndex];
      this.$emit("test", [this.myLetter, this.items[this.currentLetterIndex]]);
    },
    letterDown() {
      this.currentLetterIndex--;
      this.currentLetterIndex = ((this.currentLetterIndex % 26) + 26) % 26;
      this.selectedLetter = this.items[this.currentLetterIndex];
      this.$emit(
        "test",
        [this.myLetter, this.items[this.currentLetterIndex]],
        {}
      );
    },
  },
};
</script>

<style>
.selector {
  display: flex;
  flex-direction: column;
}

/* CSS */
.select-btn {
  background-color: #56a19d;
  border-radius: 8px;
  border-style: none;
  color: #ffffff;
  height: 30px;
  width: 30px;
  text-align: center;
  text-decoration: none;
  transition: color 100ms;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
}

.select-btn:hover {
  background-color: #76a5a3;
}

.selected-letter {
  font-family: system-ui;
  font-weight: 500;
  font-size: 20px;
  margin-top: 5px;
  margin-bottom: 5px;
}

.letters {
  font-size: 30px;
  margin-bottom: 10px;
}
</style>
