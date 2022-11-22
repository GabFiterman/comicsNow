<template>
    <v-menu transition="slide-x-transition" bottom right>
        <template v-slot:activator="{ on, attrs }">
            <div v-bind="attrs" v-on="on">
                <v-icon class="SearchType_icon">mdi-menu-down</v-icon>
            </div>
        </template>

        <!-- floating items -->
        <v-list>
            <v-list-item v-for="(item, i) in items" :key="i" v-model="items.title"  @click="changeType(item.title)" >
                <v-list-item-title >{{ item.title }}</v-list-item-title>
            </v-list-item>
        </v-list>
    </v-menu>
</template>

<script>
export default {
    name: 'SearchType',
    data() {
        return {
            switchControl: true,
            searchType: 'characters',
            items: [
                { title: "characters" },
                { title: "comics" },
            ],
        }
    },

    methods: {
        changeType(type) {
            this.searchType = type;
        },
    }
}
</script>

<style lang="scss" scoped>
.SearchType_icon{
    color: white;
}
</style>