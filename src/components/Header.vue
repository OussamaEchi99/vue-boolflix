<template>
    <header>
        <div class="container">
            <div class="logo">
                <img src="../assets/img/Netflix_2015_logo.svg" alt="">
            </div>
            <div>
                <input v-model="searchText" type="text">
                <button @click="$emit('searchNameFilm', searchText )">Cerca</button>
            </div>
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
@import "../style/Common.scss";

    header{
        height: 55px;
        background-color: #000;
        

        .container{
            display: flex;
            justify-content: space-between;
            align-items: center;
            height: 100%;

            .logo{
                img{
                    width: 13%;
                }
            }
        }
    }
</style>