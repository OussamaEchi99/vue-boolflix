<template>
    <div class="film">
        <div class="film_image">
            <img v-if="detailsSearch.backdrop_path" :src="'https://image.tmdb.org/t/p/w342'+ detailsSearch.backdrop_path" alt="">
            <div v-else>{{ checkName() }}</div>
            <div class="layover"></div>
        </div>
        <div class="film_info">
            <span>Titolo: {{ checkName() }}</span>
            <span>Titolo Originale: {{ checkOriginalName() }}</span>
            <div class="language">
                <span>Lingua Originale:</span>
                <img v-if="cherckLanguageImage()" :src="require('../assets/img/'+ detailsSearch.original_language +'.svg')" alt="">
                <span v-else>{{ detailsSearch.original_language }}</span>
            </div>
            <div class="rating">
                <span>Voto: </span>
                <span v-for="n in 5" :key="n"><i v-if="n <= rating()" class="fas fa-star yellow"></i><i v-else class="far fa-star"></i></span>
            </div>
            <span>{{ detailsSearch.overview }}</span>
        </div>
    </div>
</template>

<script>
export default {
    name: 'FilmCard',
    data: function () {
        return {
            flags: ['ar', 'en', 'fr', 'it', 'ja'],
        }
    },
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
        cherckLanguageImage: function () {
            if (this.flags.includes(this.detailsSearch.original_language)) {
                return true
            } else {
                return false
            }
        }
    }
}
</script>

<style lang="scss" scoped>
    .film {
        width: 310px;
        display: flex;
        align-items: center;
        margin: 0 5px;
        flex-shrink: 0;
        position: relative;
        overflow-y: auto;
        font-size: 13px;

        .film_image{
            position: relative;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 20px;
            width: 100%;
            font-weight: bold;
            text-transform: uppercase;
            height: 100%;
            
            .layover{
                display: none;
                width: 100%;
                height: 100%;
                background-color: black;
                position: absolute;
                top: 0;
                left: 0;
                opacity: 0.9;
            }
        }


        .film_info{
            flex-direction: column;
            position: absolute;
            display: none;
            top: 20px;
            left: 5px;

            *{
                margin: 1px 0;
            }

            .rating{
                .yellow {
                    color: #ffe100;
                }
            }
        }
        
        &:hover{
            .film_image{

                .layover{
                    display: block;
                }
            }

            .film_info{
                display: flex;
                z-index: 2;
            }
        }

        .language{
            display: flex;

            img{
                max-width: 23px;
            }
        }

            
    }
</style>