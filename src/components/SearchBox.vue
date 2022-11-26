<template>
    <v-container fluid>
        <v-row>
            <v-col cols="11">
                <input class="SearchBox-input" placeholder="Searching for Characters" />
            </v-col>

            <v-col cols="1">
                <search-type />
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
import SearchType from './SearchType.vue';

export default {
    name: 'SearchBox',
    components: {
        SearchType,
    },

    data() {
        return {
            radioGroup: 1,
        }
    },

}
</script>

<style lang="scss" scoped>
.SearchBox-input {
    background-color: rgba(50, 0, 0, .55);
    font-size: 0.85rem;
    padding: .65rem 1.25rem;
    outline: none;
    border-radius: 2rem;
    color: white;
    width: 100%;

    &:focus {
        background-color: rgba(50, 0, 0, .9);
    }

    &::placeholder {
        color: rgba(255, 255, 255, .35);
    }
}

.SearchBox {
    display: flex;
    flex-direction: row;
    justify-content: end;
    align-items: center;
    width: 100%;

    .SearchBox-radioGroup {
        display: flex;
    }
}
</style>