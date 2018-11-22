<template>
  <div id="app">
    <HelloWorld :value="phoneNumber" :defaultCountry="defaultCountry"  @formatedNumber="getPhoneNumber"/>
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
      defaultCountry: ''
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
  created() {
      let phoneNumberInfo = parsePhoneNumber("+4799999999");
      
      if (phoneNumberInfo && phoneNumberInfo.nationalNumber && phoneNumberInfo.country) {
          this.phoneNumber = phoneNumberInfo.nationalNumber;
          this.defaultCountry = phoneNumberInfo.country
      }

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
