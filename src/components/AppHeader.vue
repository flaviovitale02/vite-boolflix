<script>
import { store } from "../store";

export default {
    data() {
        return {
            store,
        };
    },

    methods: {
        emitSearchBar() {
            this.$emit('searchPerformed');
        },
    },
};
</script>

<template>
    <header>
        <nav>
            <div>
                <h1>BOOLFLIX</h1>
            </div>

            <div class="search">
                <input type="text" placeholder="Cerca Film o SerieTV" v-model="store.SearchBar"
                    @keyup.enter="emitSearchBar" />
                <button @click="emitSearchBar">CERCA</button>
            </div>
        </nav>
    </header>
</template>

<style lang="scss" scoped>
nav {
    height: 7rem;
    padding: 2rem;
    display: flex;
    align-items: center;
    justify-content: space-between;
    background-color: black;
    color: red;
}

h1 {
    color: red;
    font-size: 3rem;
}

.search {


    input,
    button {
        margin-right: 1rem;
        font-size: 2rem;
    }
}
</style>