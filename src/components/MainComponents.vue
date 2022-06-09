<template>
  <main>
      <div class="film-list">
          <p v-for="(films, index) in films" :key="index">{{films.title}}</p>
      </div>
  </main>
</template>

<script>
import axios from 'axios';
export default {
    name: 'MainComponents',
    data() {
        return {
            films: [],
        }
    },
    created() {
        axios.get('https://api.themoviedb.org/3/search/movie', {
            params: {
                api_key: '26482de69908ad7123b259cea927ba24',
                query: 'ritorno',
                language: 'it-IT',
            }
        }).then((response) => {
            this.films = response.data.results;
        }).catch((error) => {
            console.log(error);
        })
    },
}
</script>

<style lang="scss" scoped>
.film-list{
    height: 100%;
    width: 100%;
}
</style>