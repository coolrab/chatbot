<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
    </v-app-bar>
      

     

    

    <v-main>
      <div class="d-flex align-center">
       <amplify-chatbot :chatbotConfig="chatbotConfig"></amplify-chatbot>
      </div>
    </v-main>
  </v-app>
</template>

<script>

import {Interactions} from 'aws-amplify';
export default {
  name: 'App',

  data: () => ({
    chatbotConfig: {
      bot:"OrderFlowers_dev",
      clearComplete: false
    }
  }),
  mounted() {
    Interactions.onComplete("OrderFlowers_dev", this.handelComplete)
  },
  methods: {
    handelComplete(error, confirmation) {
      if(error) {
        alert(error);
        return
      }
      alert(JSON.stringify(confirmation));
    }
  }
};
</script>
