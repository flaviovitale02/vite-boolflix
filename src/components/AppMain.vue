<script>
import { store } from "../store";
import AppMovies from "./AppMovies.vue";
import AppTvSeries from "./AppTvSeries.vue";

export default {
    data() {
        return {
            store,
        };
    },

    components: {
        AppMovies,
        AppTvSeries,
    },
};
</script>

<template>
    <div class="main_container">

        <div class="movie_container">

            <h2>MOVIES</h2>

            <div class="movies">
                <AppMovies v-for="movies in store.ArrMovies" :key="movies.id" :poster_path="movies.poster_path"
                    :title="movies.title" :original_title="movies.original_title"
                    :original_language="movies.original_language" :vote_average="movies.vote_average" />
            </div>
        </div>



        <div class="series_container">

            <h2>SERIE TV</h2>


            <div class="series">
                <AppTvSeries v-for="series in store.ArrTvSeries" :key="series.id" :poster_path="series.poster_path"
                    :name="series.name" :original_name="series.original_name" :original_language="series.original_language"
                    :vote_average="series.vote_average" />
            </div>
        </div>



    </div>
</template>

<style lang="scss" scoped>
h2 {
    margin-top: 1rem;
    margin-bottom: 1rem;
    font-size: 3rem;
    margin-left: 4rem;
}

.main_container {
    background-color: rgb(47, 47, 47);
    color: beige;
}

.movie_container,
.series_container {
    overflow-y: auto;
    padding-top: 4rem;

}

.movies,
.series {
    display: flex;
}
</style>
