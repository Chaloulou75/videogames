<template>
  <div class="container py-16 mx-auto">
    <h1 class="mb-8 font-bold uppercase">Popular Games</h1>
    <div class="flex flex-wrap -mx-4 game-container">
      <nuxt-link :to="'/games/' + game.id" v-for="game in games" :key="game.id" class="w-full px-4 mb-12 no-underline md:w-1/5">
        <img :src="game.cover.url.replace('t_thumb', 't_cover_big')" alt="cover">
        <div class="overflow-hidden text-lg font-semibold text-black whitespace-no-wrap overflow-dots">{{ game.name }}</div>
        <div class="pb-1 overflow-hidden text-base text-gray-900 whitespace-no-wrap overflow-dots">{{ game.genres[0].name }}</div>
      </nuxt-link>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  components: {
  },
  asyncData ({ params, error }) {
    const proxyurl = 'https://cors-anywhere.herokuapp.com/'
    return axios.get(`${proxyurl}https://api-v3.igdb.com/games/?fields=name,genres.name,cover.url,popularity&order=popularity:desc&expand=genres`)
    .then((res) => {
      return {
        games: res.data
      }
    })
    .catch((e) => {
      console.log(e)
    })
  },
  data() {
    return {
      games: []
    }
  }
}
</script>

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
@apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/

</style>
