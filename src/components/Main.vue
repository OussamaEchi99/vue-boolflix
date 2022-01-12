<template>
    <main>
        <h2>Films</h2>
        <FilmCard v-for="filmInfo in detailsSearchMovies" :key="filmInfo.id" :detailsSearch="filmInfo"/>

        <h2>Series TV</h2>
        <FilmCard v-for="seriesTVInfo in detailsSearchSeriesTV" :key="seriesTVInfo.id" :detailsSearch="seriesTVInfo"/>
    </main>
</template>

<script>
import FilmCard from "./FilmCard.vue";

export default {
    name: 'Main',
    components: {
        FilmCard
    },
    props: {
        detailsSearchMovies: Array,
        detailsSearchSeriesTV: Array
    }
}
</script>

<style lang="scss" scoped>
    main{
        display: flex;
        width: 60%;
        margin: auto;
        flex-direction: column;
        flex-wrap: wrap;

        
    }
</style>