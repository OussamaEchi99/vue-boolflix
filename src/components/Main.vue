<template>
    <main>
        <div v-for="(filmInfo, index) in detailsSearch" :key="index" class="film">
            <span>{{ filmInfo.title }}</span>
            <span>{{ filmInfo.original_title }}</span>
            <span>{{ filmInfo.original_language }}</span>
            <span>{{ filmInfo.vote_average }}</span>
        </div>
    </main>
</template>

<script>
export default {
    name: 'Main',
    props: {
        detailsSearch: Array
    }
}
</script>

<style lang="scss" scoped>
    main{
        display: flex;
        width: 60%;
        margin: auto;
        flex-wrap: wrap;

        .film {
            min-width: calc(100% / 5);
            margin: 10px;
            display: flex;
            flex-direction: column;
        }
    }
</style>