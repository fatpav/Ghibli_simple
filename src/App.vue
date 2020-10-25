<template>
  <main>
    <header>
      <h1>Welcome to the Ghibli film selector!</h1>
      <h2>Pick a film from the box to learn more about Ghibli releases.</h2>
      </header>
      <section>
          <form>
            <select name="films" id="film-selector" v-model="selectedFilm">
              <option value="" disabled selected>-- Pick a Film! --</option>
              <option v-for="(film, index) in films" :key="index" :value="film">{{film.title}}</option>
            </select>
          </form>
          <film-detail :film='selectedFilm'></film-detail>
      </section>
    
    <footer>
      <h2>Made (poorly) by Paul D</h2>
    </footer>
  </main>
</template>

<script>

import {eventBus} from '@/main.js';
import filmsList from './components/filmList.vue'
import filmDetail from './components/filmDetail.vue'


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
      .then(films => this.films = films)
    eventBus.$on('film-selected', (film) => {
      this.selectedFilm = film;
      })
    }
  },
  components: {
    // 'film-list': filmList,
    'film-detail': filmDetail
  }
}
</script>

<style lang='css' scoped>
.app {
  width: 40%;
  
}

main {

  margin:auto;
  font-family: fantasy;
  position:fixed;
    top:0;
    bottom:0;
    left:0;
    right:0;

  display: flexbox;
  grid-template-rows: 800px auto 800px;
  min-block-size: 400px;

  
  background-image: url('https://i.pinimg.com/originals/04/14/be/0414be174bc8755e5ded5460daf039e5.png');
  
}

header {

  text-align: center;
  font-family: fantasy;

  grid-area: header;
  display: grid-row;
  justify-content: space-between; 
  align-items: center;
}

footer {
  grid-area: footer;
  align-items: center;
  position: absolute;
  bottom: 0;
  width: 100%;
  height: 2.5rem;
  margin:auto; 
}

</style>