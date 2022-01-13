<template>
    <main>
        <div class="container">
            <div class="movies">
                <h2 v-if="detailsSearchMovies.length">Films</h2>
                <div v-if="detailsSearchMovies.length > 0" class="movies_card">
                    <FilmCard v-for="filmInfo in detailsSearchMovies" :key="filmInfo.id" :detailsSearch="filmInfo"/>
                </div>
            </div>

            <div class="series_tv">
                <h2 v-if="detailsSearchSeriesTV.length">Series TV</h2>
                <div class="series_tv_card">
                    <FilmCard v-for="seriesTVInfo in detailsSearchSeriesTV" :key="seriesTVInfo.id" :detailsSearch="seriesTVInfo"/>
                </div>
            </div>
        </div>
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
@import "../style/Common.scss";

    main{
        display: flex;
        align-items: flex-start;
        height: calc(100vh - 55px);
        background-color: #141414;

        .container{
            display: flex;
            flex-direction: column;
            justify-content: flex-start;
            margin: 0 auto;
            height: 100%;

            h2{
                margin-bottom: 10px;
            }

            .movies{
                margin-top: 10px;

                .movies_card{
                    display: flex;
                    overflow-x: auto;
                }
            }

            .series_tv{
                margin-top: 50px;

                .series_tv_card{
                    display: flex;
                    overflow-x: auto;
                }
            }
        }
        
    }
</style>