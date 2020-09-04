<template>
  <div>
    <Navigation />
    <Nuxt />
  </div>
</template>

<script>
import Navigation from '@/components/Navigation'
import axios from 'axios'

axios.defaults.headers.common['user-key'] = 'c94983d390777b43a36b585a3ce94e0d'
axios.defaults.headers.common['X-Requested-With'] = 'XMLHttpRequest'

export default {
  components: {
    Navigation
  }
}
</script>

<style>

</style>
