<template>
  <div class="container">
    <div class="d-flex search">
      <form @submit.prevent="fetchSearchedMovies">
        <SearchMovie v-model="searchInput" />
        <button class="button">Search</button>
        <button v-if="searchInput" class="button" @click="clearSearch">
          Clear
        </button>
      </form>
    </div>
    <div id="movie-grid" class="movie-grid">
      <Loading v-if="$fetchState.pending" />
      <Movie v-for="movie in movies" v-else :key="movie.id" :movie="movie" />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      searchInput: '',
      movies: [],
      moviesBackup: [],
    }
  },
  async fetch() {
    await this.fetchMovies()
  },
  methods: {
    async fetchMovies() {
      const data = await fetch(
        `https://api.themoviedb.org/3/movie/now_playing?api_key=${process.env.THEMOVIEDB_API}`
      )
      const json = await data.json()
      this.movies = json.results
      this.moviesBackup = json.results
    },
    async fetchSearchedMovies() {
      const data = await fetch(
        `https://api.themoviedb.org/3/search/movie?api_key=${process.env.THEMOVIEDB_API}&language=en-US&page=1&query=${this.searchInput}`
      )
      const json = await data.json()
      this.movies = json.results
    },
    clearSearch() {
      this.searchInput = ''
      this.movies = this.moviesBackup
    },
  },
}
</script>

<style lang="scss" scoped>
.movie-grid {
  display: grid;
  // grid-template-columns: 1fr 1fr 1fr;
  column-gap: 30px;
  row-gap: 30px;
  padding: 50px 0;
  @media (min-width: 500px) {
    grid-template-columns: repeat(2, 1fr);
  }
  @media (min-width: 750px) {
    grid-template-columns: repeat(2, 1fr);
  }
  @media (min-width: 1100px) {
    grid-template-columns: repeat(4, 1fr);
  }
}
.search {
  margin-top: 50px;
}
</style>
