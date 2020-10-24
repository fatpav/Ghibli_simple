<template>
  <h1>Welcome to a bunch of stuff about Ghibli films!</h1>
</template>

<script>
export default {
  name: 'app',
  data() {
    return {
      films: [],
      selectedFilm: null
    }
  },
  mounted() {
    this.fetchFilms()
  },

  methods: {
    fetchFilms: function () {
      const request = fetch('https://ghibliapi.herokuapp.com/films')
      .then(response => response.json())
      .then(data => this.data = films)
    }
  }
}
</script>

<style lang='css' scoped>
.app {
  width: 40%;
}
</style>