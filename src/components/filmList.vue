<template>
  <section>
      <ul>
          <film-list v-for='(film, index) in films' :films='film' :key='index'></film-list>
      </ul>
  </section>
</template>

<script>
import filmSelect from './filmSelector.vue'
export default {
    name: 'film-list',
    props: ['films'],
    components: {
        'film-select': filmSelect
    }

}
</script>

<style>

</style>