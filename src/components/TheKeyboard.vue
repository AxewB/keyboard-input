<template>
  <div class="the-keyboard">
    <KeyboardKey 
      v-for="(kbKey, kbKeyName) in keys" 
      :key="kbKeyName" 
      :keyText="kbKeyName"
      :clickedKey="kbKeyName"
      :isPressed="kbKey"
      />
  </div>
</template>

<script>
import KeyboardKey from './KeyboardKey.vue'
export default {
  name: "TheKeyboard",
  components: {
    KeyboardKey
  },
  data() {
    return {
      keys: {
        'escape': false,
        'f1': false,
        'f2': false,
        'f3': false,
        'f4': false,
        'f5': false,
        'f6': false,
        'f7': false,
        'f8': false,
        'f9': false,
        'f10': false,
        'f11': false,
        'f12': false,
        'backquote': false,
        '1': false,
        '2': false,
        '3': false,
        '4': false,
        '5': false,
        '6': false,
        '7': false,
        '8': false,
        '9': false,
        '0': false,
        '-': false,
        '=': false,
        'backspace': false,
        'tab': false,
        'q': false,
        'w': false,
        'e': false,
        'r': false,
        't': false,
        'y': false,
        'u': false,
        'i': false,
        'o': false,
        'p': false,
        '[': false,
        ']': false,
        '\\': false,
        'capslock': false,
        'a': false,
        's': false,
        'd': false,
        'f': false,
        'g': false,
        'h': false,
        'j': false,
        'k': false,
        'l': false,
        ';': false,
        "'": false,
        'enter': false,
        'shift': false,
        'z': false,
        'x': false,
        'c': false,
        'v': false,
        'b': false,
        'n': false,
        'm': false,
        ',': false,
        '.': false,
        '/': false,
        'shift': false,
        'control': false,
        'alt': false,
        'space': false,
        'alt': false,
        'meta': false,
        'contextmenu': false,
        'control': false,
        'arrowUp': false,
        'arrowdown': false,
        'arrowleft': false,
        'arrowright': false,
        'insert': false,
        'delete': false,
        'home': false,
        'end': false,
        'pageup': false,
        'pagedown': false,
        'numlock': false,
      },
      currentKey: '',
    }
  },
  beforeMount() {
    addEventListener("keydown", (event) => {
      this.keys[event.key.toLowerCase()] = true

      if (event.key.toLowerCase() === "capslock") {
        this.keys[event.key.toLowerCase()] = !this.keys[event.key.toLowerCase()]
      }
    });

    addEventListener("keyup", (event) => {
      this.keys[event.key.toLowerCase()] = false
    })

  }
}
</script>

<style scoped>
.the-keyboard {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  width: 500px;
  height: 300px;
}
</style>