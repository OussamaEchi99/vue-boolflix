<template>
    <header>
        <div>
            <input v-model="searchText" type="text">
            <button @click="$emit('searchNameFilm', searchText )">Cerca</button>
        </div>
    </header>
</template>

<script>
export default {
    name: 'Header',
    data: function () {
        return {
            searchText: ''
        };
    },
}
</script>

<style lang="scss" scoped>
    header{
        height: 100px;
        background-color: black;
        display: flex;
        justify-content: center;
        align-items: center;
    }
</style>