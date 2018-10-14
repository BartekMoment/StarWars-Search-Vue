<template>
  <div id="app">
      <v-app dark>
        <v-container grid-list-xl text-xs-center>
          <v-layout row wrap>
            <v-flex>
                <Searach/>
            </v-flex>
          </v-layout>
        </v-container>
        <v-footer class="pa-3">
          <v-spacer></v-spacer>
          <div>&copy; {{ new Date().getFullYear() }}</div>
        </v-footer>
    </v-app>
  </div>
</template>

<script>
// index.js or main.js
import 'vuetify/dist/vuetify.min.css' // Ensure you are using css-loader
import '@fortawesome/fontawesome-free/css/all.css'
import Searach from './components/search'


export default {
  name: 'app',
  components: {
    Searach
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Montserrat:300,400,500i,600,700,800i');
</style>
