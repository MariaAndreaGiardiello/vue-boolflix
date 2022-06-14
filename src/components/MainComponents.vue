<template>
  <main>
      <form @submit.prevent="searching">
            <input type="text" v-model="searchText">
            <button type="button">Search</button>
      </form>
      <ul>
        <li v-for="movie in data.movies" :key="movie.id">
            <h3>{{movie.title}}</h3>
            <h5>{{movie.original_title}}</h5>
            <h5>{{movie.vote_average}}</h5>
            <p>
                <img v-if="existFlag(movie.original_language)" :src="require(`../assets/flags/${movie.original_language}.png`)">
                <img v-else src="../assets/flags/peace.png">
            </p>
        </li>
      </ul>
  </main>
</template>

<script>
import axios from 'axios';
import data from '../components/shared/data';
export default {
    name: 'MainComponents',
    data() {
        return {
            data,
            searchText: '',
            flagsAvaible: [
                'en',
                'peace',
                'chi',
                'ja',
                'it',
                'pt',
                'es',
                'de',
                'fr',
            ]

        }
    },
    methods: {
        searching(){
            axios.get('https://api.themoviedb.org/3/search/movie', {
            params: {
                api_key: '26482de69908ad7123b259cea927ba24',
                query: this.searchText,
                language: 'it-IT',
            }
        }).then((response) => {
            data.movies = response.data.results;
        }).catch((error) => {
            console.log(error);
        })
        },

        existFlag(lang) {
            return this.flagsAvaible.includes(lang);
        }
    }
}
</script>

<style lang="scss" scoped>
.film-list{
    height: 100%;
    width: 100%;
}
</style>