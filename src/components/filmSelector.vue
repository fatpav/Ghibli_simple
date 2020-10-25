<template lang='html'>
<li v-on:click='handleClick'> {{film.title}} </li>
  
</template>

<script>
import { eventBus } from '@/main.js'
export default {
    name: 'film-select',
    props: ['film'],
    methods: {
        handleClick: function () {
            eventBus.$emit('film-selected', this.film)
        }
    }
}
</script>

<style>

</style>