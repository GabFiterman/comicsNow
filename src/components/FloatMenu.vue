<template>
    <v-menu transition="slide-x-transition" bottom right>
        <template v-slot:activator="{ on, attrs }">
            <div v-bind="attrs" v-on="on">
                <v-app-bar-nav-icon color="white"></v-app-bar-nav-icon>
            </div>
        </template>

        <!-- floating left menu items -->
        <v-list>
            <v-list-item v-for="(item, i) in items" :key="i">
                <v-list-item-title>{{ item.title }}</v-list-item-title>
            </v-list-item>
        </v-list>
    </v-menu>
</template>

<script>
export default {
    name: 'FloatMenu',

    data() {
        return {
            items: [
                { title: "Click Me" },
                { title: "Click Me" },
                { title: "Click Me" },
                { title: "Click Me 2" },
            ],
        }
    }
}
</script>

<style lang="scss" scoped>
// .v-sheet.v-app-bar.v-toolbar:not(.v-sheet--outlined) {
//     background-color: $color_invisible;
// }
</style>