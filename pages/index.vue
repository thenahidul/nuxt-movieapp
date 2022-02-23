<template>
  <Movies />
</template>

<script>
export default {
  name: 'IndexPage',
  head() {
    return {
      title: 'Movie APP - Latest Streaming Movie Information',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'Get all the latest streaming movies in theaters & online',
        },
        {
          hid: 'keywords',
          name: 'keywords',
          content: 'movies, stream, stremaing',
        },
      ],
    }
  },
}
</script>
