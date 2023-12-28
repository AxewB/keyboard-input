<template>
  <div class="keyboard-key">
    <div class="keyboard-key-base" :class="isPressed ? 'kb-key-pressed' : 'kb-key-inactive'">
      <div class="keyboard-key-base-inner">
      {{ keyText }}

      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "KeyboardKey",
  props: {
    keyText: String,
    clickedKey: String,
    size: Number, // small / medium / large
    isPressed: {type: Boolean, default: false},
  },
}
</script>

<style scoped>
.kb-key-inactive {
  background-color: black;
}

.kb-key-pressed {
  background-color: gray;
}

.keyboard-key-base { 
  display: flex; 
  
  justify-content: center;
  align-items: center;

  height: 50px;
  width: 50px;

  border: 1px solid gray;
  border-radius: 5px;
}

.keyboard-key-base-inner { 
  display: flex; 
  
  justify-content: center;
  align-items: center;
  
  width: 75%;
  height: 75%;

  /* border: inherit; */
  border-radius: inherit;
}
</style>