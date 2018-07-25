,<template>
    <v-app dark>
    <v-container grid-list-xl text-xs-center>
        <v-layout row wrap>
        <v-flex md8 offset-xs2>
            <v-card dark>
                <v-card-text>
                    <img style="width:200px;" src="../assets/star_wars_logo.png"/>
                    <v-flex md6 offset-xs3>
                        <v-text-field
                            color="yellow"
                            name="input-1"
                            label="Wyszukaj"
                            v-model="query"
                            hint="Naciśnij ESC aby skasować wyszukiwanie"
                            ></v-text-field>
                        </v-flex>
                        <v-progress-circular indeterminate v-bind:size="50"  color="yellow" v-if="isSearching"></v-progress-circular>
                        <v-list v-else-if="resultsPeople.length > 0">
                            <v-list-tile v-for="person in people"
                                        :key="person.id"
                                        >Nazwa postaci: {{ person }}
                            </v-list-tile>
                        </v-list>
                </v-card-text>
            </v-card>
        </v-flex>
        </v-layout>
    </v-container>
    </v-app>
</template>


<script>

// index.js or main.js
import 'vuetify/dist/vuetify.min.css' // Ensure you are using css-loader

export default {
    name: 'search',
    data() {
        return {
            query: '',
            resultsPeople: [],
            isSearching: false
        }
    },
    watch: {
        query: function(value) {
            this.search(value)
        }
    },
    methods: {
        search: function (query) {
        this.isSearching = true;
        axios.get('https://swapi.co/api/people/', {params: {search: query}})
            .then((response) => {
                console.log(response.data.results);
                this.resultsPeople = response.data.results.map((x) => x.name );
                this.isSearching = false;

            })
        }
    }

}
</script>



