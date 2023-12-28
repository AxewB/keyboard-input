<template>
  <div>
    <TheKeyboard v-if="false"/>
    <TypeTester/>
  </div>
</template>

<script>
import TheKeyboard from './components/TheKeyboard.vue'
import TypeTester from './components/TypeTester.vue';
export default {
  name: "App",
  components: {
    TheKeyboard,
    TypeTester
  },

}
</script>
