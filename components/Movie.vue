<template>
  <div class="movie">
    <figure>
      <div>
        <NuxtLink :to="{ name: 'movie-id', params: { id: movie.id } }">
          <img
            :src="`https://image.tmdb.org/t/p/w500/${movie.poster_path}`"
            :alt="movie.title"
          />
        </NuxtLink>
        <div class="rating">{{ movie.vote_average }}</div>
        <div class="overview">
          {{
            movie.overview.length >= 100
              ? movie.overview.slice(0, 100) + '...'
              : movie.overview
          }}
        </div>
      </div>
      <figcaption>
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
      </figcaption>
    </figure>
    <NuxtLink
      :to="{ name: 'movie-id', params: { id: movie.id } }"
      class="button button-light btn-link"
      >More Info</NuxtLink
    >
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
  //   border: 1px solid #e3e3e3;
  //   padding: 5px;
  border-radius: 5px;
  img {
    max-width: 100%;
  }
  figure > div {
    position: relative;
    overflow: hidden;
    .rating,
    .overview {
      position: absolute;
      bottom: 0;
      left: 0;
      right: 0;
      background-color: crimson;
      padding: 20px;
    }
    .rating {
      right: auto;
      left: 0;
      bottom: auto;
      top: 0;
      padding: 10px 15px;
      border-radius: 0 10px;
    }
    .overview {
      opacity: 0;
      transform: translateY(100%);
      transition: all 0.5s;
    }
    &:hover .overview {
      opacity: 1;
      transform: translateY(0);
    }
  }
  h2 {
    font-size: 1.5rem;
  }
  .button {
    margin-top: 15px;
  }
}
</style>
