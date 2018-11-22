<template>
  <div id="app">
    <HelloWorld value="" @formatedNumber="getPhoneNumber"/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';

import { parsePhoneNumber } from 'libphonenumber-js'

export default {
  name: 'app',
    data() {
    return {
      phoneNumber: '',
    };
  },
  components: {
    HelloWorld
  },
  methods: {
    getPhoneNumber(number) {
        console.log("number", number)
    }
  },
  mounted() {
      let tree = parsePhoneNumber("+08801683902204");
      console.log("trre", tree);
  },
}
</script>


<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
