<template>
<article v-if="film">
    <h3>Title: {{film.title}}</h3>
    <h4>Director: {{film.director}}</h4>
    <p>Description: {{film.description}}</p>
</article>
  
</template>

<script>
export default {
    name: 'film-detail',
    props: ['film']

}
</script>

<style>

</style>