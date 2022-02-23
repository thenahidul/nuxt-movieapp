<template>
  <div class="d-flex align-center movie">
    <div class="left">
      <img
        :src="`https://image.tmdb.org/t/p/w500/${movie.poster_path}`"
        :alt="movie.title"
      />
      <div class="rating">{{ movie.vote_average }}</div>
    </div>
    <div class="right">
      <h2>{{ movie.title }}</h2>
      <p>
        Released:
        {{
          new Date(movie.release_date).toLocaleDateString('en-US', {
            month: 'long',
            day: 'numeric',
            year: 'numeric',
          })
        }}
      </p>
      <p class="movie-fact tagline">
        <span>Tagline:</span> "{{ movie.tagline }}"
      </p>
      <p class="movie-fact">
        <span>Duration:</span> {{ movie.runtime }} minutes
      </p>
      <p class="movie-fact">
        <span>Revenue:</span>
        {{
          movie.revenue.toLocaleString('en-us', {
            style: 'currency',
            currency: 'USD',
          })
        }}
      </p>
      <p class="movie-fact"><span>Overview:</span> {{ movie.overview }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    movie: {
      type: Object,
      default: () => ({}),
    },
  },
}
</script>

<style lang="scss" scoped>
.movie {
  margin: 30px 0;
  @media (max-width: 1024px) {
    flex-direction: column;
  }

  .left {
    position: relative;
    @media (min-width: 1024px) {
      width: 40%;
    }
    @media (max-width: 1024px) {
      margin-bottom: 30px;
    }
    .rating {
      position: absolute;
      top: 0;
      right: 0;
      background-color: crimson;
      padding: 10px 15px;
      border-radius: 0 10px;
    }
  }
  .right {
    padding: 0 30px;
    h2 {
      font-size: 2rem;
    }
    p {
      font-size: 1.2rem;
      font-weight: 300;
      margin: 10px 0;
    }
    @media (min-width: 1024px) {
      width: 60%;
    }
  }
}
</style>
