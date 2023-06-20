<template>
  <v-app>
    <v-app-bar app color="deep-purple accent-4">
      <v-toolbar-title>Priesthood Equality</v-toolbar-title>
    </v-app-bar>
    <Main>
      <!-- content here -->
    </Main>
    <v-footer color="deep-purple accent-4" class="white--text" fixed>
      <v-row class="text-center">
        <v-col cols="12" lg="6">
          © 2023 June Lewis
        </v-col>
        <v-col cols="12" lg="6">
          Follow me on 
          <a href="https://twitter.com/Junee63062915" target="_blank" class="white--text">
            Twitter
          </a>
        </v-col>
        <v-col cols="12">
          All contents on this site are properties of June Lewis.
        </v-col>
      </v-row>
    </v-footer>
  </v-app>
</template>

<script>
import Main from './components/Main.vue'
export default {
  data() {
    return {
      drawer: false
    }
  },
  components: {
    Main
  }
}
</script>
<style>
.v-footer {
  padding: 10px 0;
  
}
</style>