<template>
  <main>
      <form @submit.prevent="searching">
            <input type="text" v-model="searchText">
            <button type="button">Search</button>
      </form>
  </main>
</template>

<script>
import axios from 'axios';
export default {
    name: 'MainComponents',
    data() {
        return {
            searchText: '',
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
            console.log(response.data.results);
        }).catch((error) => {
            console.log(error);
        })
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