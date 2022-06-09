<template>
  <main></main>
</template>

<script>
import axios from 'axios';
export default {
    name: 'MainComponents',
    created() {
        axios.get('https://api.themoviedb.org/3/search/movie', {
            params: {
                api_key: 'e99307154c6dfb0b4750f6603256716d',
                query: 'ritorno',
                language: 'it-IT',
            }
        }).then((response) => {
            console.log(response.data.results);
        }).catch((error) => {
            console.log(error);
        })
    },
}
</script>

<style lang="scss" scoped>

</style>