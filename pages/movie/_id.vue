<template>
  <div class="container">
    <Loading v-if="$fetchState.pending" />
    <template v-else>
      <NuxtLink to="/" class="button">BACK</NuxtLink>
      <MovieSinglePage class="movie-single-page" :movie="movie" />
    </template>
  </div>
</template>

<script>
export default {
  data() {
    return {
      pageTitle: '',
      movie: {},
    }
  },
  async fetch() {
    await this.fetchMovie()
  },
  head() {
    return {
      title: this.pageTitle,
    }
  },
  methods: {
    async fetchMovie() {
      const data = await fetch(
        `https://api.themoviedb.org/3/movie/${this.$route.params.id}?api_key=${process.env.THEMOVIEDB_API}`
      )
      const json = await data.json()
      this.movie = json
      this.pageTitle = this.movie.title
    },
  },
}
</script>

<style lang="scss" scoped>
.button {
  margin: 30px 0 0;
}
</style>
