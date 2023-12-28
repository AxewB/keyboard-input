<template>
  <div class="words-wrapper">
    <div class="word" 
          v-for="(word, indexWord) in words" 
          :key="word + indexWord + ''">
      <div :class="typed && typed[indexLetter] == letter && indexWord == typedWords.length ? 'letter-success' : 'letter-error'" 
            v-for="(letter, indexLetter) in word" 
            :key="'' + letter + indexWord + indexLetter + Date.now()" 
            @click = "logging('' + letter + indexWord + indexLetter + Date.now())">
        {{ letter }}
      </div>
      <div>&nbsp;</div>
    </div>
    {{ typed }}
    {{ typedWords }}
  </div>
  <div class="words-wrapper">
    <div class="word" v-for="(word, indexWord) in typedWords" :key="word + indexWord + ''">
      <div class="letter" v-for="(letter, indexLetter) in word" :key="letter + indexWord + indexLetter + ''">{{ letter }}</div>
      <div class="letter">&nbsp;</div>
    </div>
    <div class="letter" v-for="(letter, indexLetter) in typed" :key="letter + indexWord + indexLetter + ''">{{ letter }}</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      words: [
        'publish',
        'extension',
        'cultivate',
        'day',
        'piano',
        'delivery',
        'flow',
        'employ',
        'reporter',
        'monkey',
        'freeze',
        'serious',
        'cellar',
        'adoption',
        'march',
        'simplicity',
        'jurisdiction',
        'bet',
        'escape',
        'poll',
      ],
      typed: '',
      typedWords: [],
      editPrev: false,
    }
  },
  methods: {
    isLettersMatch(letterA, letterB) {
      return letterA === letterB
    },
    logging( message ){
      console.log( message )
    }
  },
  beforeMount() { 
    addEventListener("keydown", (event) => {
      console.log(event.key)
      if (event.key.toLowerCase() == ' ' && this.typed.length > 0) {
        if (this.editPrev === true) {
          this.editPrev = false;
        }
        this.typedWords.push(this.typed);
        this.typed = '';
      } 
      else if (event.key.toLowerCase() == 'backspace') {
        if (this.typed.length === 0 && this.editPrev === false) {
          this.editPrev = true;
          this.typed = this.typedWords[this.typedWords.length - 1]
          this.typedWords.pop();
        }
        else {
          this.typed = this.typed.slice(0, -1);
        }
      }
      else if (/^[a-zA-Z]+$/.test(event.key) && event.key.length === 1) {
        this.typed += event.key;
      }
    })

  }
}
</script>

<style scoped>
.words-wrapper { 
  display: flex; 
  flex-direction: row;

}

.word {
  display: flex;
}

.letter-success {
  color: green;
}

.letter-error {
  color: red;
}
</style>