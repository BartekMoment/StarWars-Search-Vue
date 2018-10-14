<template>
    <v-container grid-list-md text-xs-center>
          <v-card>
            <v-card-media 
              class="white--text"
            >
              <v-container fill-height fluid>
                <v-layout fill-height>
                  <v-flex xs12 align-end flexbox>
                    <span class="headline">{{ item.name }}</span>
                  </v-flex>
                </v-layout>
              </v-container>
            </v-card-media>
            <v-card-title>
              <div>
                <span>{{ item.birth_year }}</span><br>
                <span>{{ item.eye_color }}</span>
              </div>
            </v-card-title>
            <!-- <v-card-actions>
              <v-btn flat color="orange">Share</v-btn>
              <v-btn flat color="orange">Explore</v-btn>
            </v-card-actions> -->
          </v-card>
    </v-container>
  </template>
<script>
export default {
    name: 'itemcard',
    props: {
      item: {
        type: Object,
        required: true
      }
    }
}
</script>

<style scoped>

</style>
