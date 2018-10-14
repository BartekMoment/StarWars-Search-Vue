,<template>
    <v-card dark>
        <v-card-text>
            <img style="width:200px;" src="../assets/star_wars_logo.png"/>
            <v-flex md6 offset-xs3>
                <v-text-field
                    color="yellow"
                    name="input-1"
                    label="Wyszukaj postać"
                    append-outer-icon="search"
                    v-model="query"
                    ></v-text-field>
                </v-flex>
                <v-progress-circular indeterminate v-bind:size="50" color="yellow" v-if="isSearching"></v-progress-circular>
                <v-container grid-list-md text-xs-center v-else-if="resultsPeople.length >= 0">
                    <v-layout row wrap>
                        <div xs4>
                            <CardItem v-for="item in resultsPeople" :key="item.id" :item="item" @click.native="handleModalOpen(item)"></CardItem>
                        </div>
                    </v-layout>
                </v-container>
                    <!-- <v-list-tile v-for="person in resultsPeople"
                                :key="person.id"
                                >Nazwa postaci: {{ person.name }}
                                Wiek: {{ person.birth_year }}
                    </v-list-tile> -->
        </v-card-text>
                    <Modal v-if="modalOpen"/>
    </v-card>
</template>


<script>
import axios from 'axios';
import debounce from 'lodash.debounce'
import CardItem from './itemcard'
import Modal from './Modal'

export default {
    name: 'search',
    components: {
        CardItem,
        Modal
    },
    data() {
        return {
            modalOpen: false,
            query: '',
            resultsPeople: [],
            isSearching: false
        }
    },
    watch: {
        query: debounce(function(value) {
            this.search(value)
        }, 500)
    },
    methods: {
        handleModalOpen(item) {
            this.modalOpen = true;
        },
        search: function (query) {
        this.isSearching = true;
        axios.get('https://swapi.co/api/people/', {params: {search: query}})
            .then((response) => {
                console.log(response.data.results);
                this.resultsPeople = response.data.results;
                // this.resultsPeople = response.data.results.map((x) => x.name );
                this.isSearching = false;

            })
        }
    }

}
</script>



