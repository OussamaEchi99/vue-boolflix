<template>
    <div class="film">
        <div class="film_image">
            <img :src="'https://image.tmdb.org/t/p/w342'+ detailsSearch.backdrop_path" alt="">
        </div>
        <div class="film_info">
            <span>Titolo: {{ checkName() }}</span>
            <span>Titolo Originale: {{ checkOriginalName() }}</span>
            <div class="language">
                <span>Lingua Originale:</span>
                <img :src="require('../assets/img/'+ detailsSearch.original_language +'.svg')" alt="">
            </div>
            <div>
                <span>Voto: {{ rating() }}</span>
                <span v-for="n in 5" :key="n"><i v-if="n <= rating()" class="fas fa-star"></i><i v-else class="far fa-star"></i></span>
            </div>
            
        </div>
    </div>
</template>

<script>
export default {
    name: 'FilmCard',
    props: {
        detailsSearch: Object
    },
    methods: {
        rating: function () {
            return Math.ceil(this.detailsSearch.vote_average / 2)
        },
        checkName: function () {
            if (this.detailsSearch.title) {
                return this.detailsSearch.title
            } else {
                return this.detailsSearch.name
            }
        },
        checkOriginalName: function () {
            if (this.detailsSearch.title) {
                return this.detailsSearch.original_title
            } else {
                return this.detailsSearch.original_name
            }
        },
    }
}
</script>

<style lang="scss" scoped>
    .film {
        min-width: calc(100% / 5);
        margin: 50px 0;
        display: flex;
        align-items: center;
        border: 1px solid black;
        padding: 50px;

        .film_info{
            display: flex;
            flex-direction: column;
        }

        .language{
            display: flex;

            img{
                max-width: 11%;
            }
        }

            
    }
</style>