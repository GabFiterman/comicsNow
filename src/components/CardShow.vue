<template>
    <!-- TODO: Tornar este card mais genérico, para poder ser reutilizado não apenas pelos characters, mas por qualquer tipo de info -->
    <v-row>
        <v-col cols="6" v-for="(res, index) in API_responses" :key="index">
            <v-hover v-slot="{ hover }">
                <v-card class="mx-1 my-2" color="grey lighten-4">
                    <v-img height="75vh" :aspect-ratio="16 / 9" :src="getImage(index)">
                        <v-expand-transition>
                            <div v-if="hover"
                                class="d-flex transition-fast-in-fast-out black darken-2 v-card--reveal text-h2 white--text"
                                style="height: 100%;">

                                <v-card-text class="card-hover">
                                    <h1 class="mb-3">{{ getName(res.name) }}</h1>

                                    <v-list>
                                        <v-list-item-group v-model="selectedItem" color="white">

                                            <v-list-item>
                                                <v-list-item-content>
                                                    <v-list-item-title class="card-infoValue">
                                                        <p>Comics:</p> <span class="">{{ res.comics.available }}</span>
                                                    </v-list-item-title>
                                                </v-list-item-content>
                                            </v-list-item>

                                            <v-list-item>
                                                <v-list-item-content>
                                                    <v-list-item-title class="card-infoValue">
                                                        <p>Series:</p> <span class="">{{ res.series.available }}</span>
                                                    </v-list-item-title>
                                                </v-list-item-content>
                                            </v-list-item>

                                            <v-list-item>
                                                <v-list-item-content>
                                                    <v-list-item-title class="card-infoValue">
                                                        <p>Stories:</p> <span class="">{{ res.stories.available
                                                        }}</span>
                                                    </v-list-item-title>
                                                </v-list-item-content>
                                            </v-list-item>
                                        </v-list-item-group>
                                    </v-list>
                                    <router-link :to="`/characterPage/${getPageId(res.name)}`">
                                        <v-btn elevation="2" class="mt-4 card-btn" target="_blank">See more</v-btn>
                                    </router-link>
                                </v-card-text>
                            </div>
                        </v-expand-transition>
                    </v-img>
                </v-card>
            </v-hover>
        </v-col>
    </v-row>
</template>

<script>
export default {
    name: 'CardShow',

    props: {
        API_responses: Array
    },

    data: () => ({
        selectedItem: 1,
        items: [
            { text: 'Real-Time', icon: 'mdi-clock' },
            { text: 'Audience', icon: 'mdi-account' },
            { text: 'Conversions', icon: 'mdi-flag' },
        ],
    }),

    methods: {
        getImage(arr) {
            let imageUrl = `${this.API_responses[arr].thumbnail.path}.${this.API_responses[arr].thumbnail.extension}`
            return imageUrl;
        },
        getName(name) {
            let splited = name.split(new RegExp(/(\().+/g));

            if (splited[0].length >= 20) {
                let substring = `${splited[0].substring(0, 12)}...`
                return substring;
            }

            return splited[0];
        },
        getPageId(name) {
            let pageId = this.getName(name);
            console.log(pageId.replace(/[^A-Z0-9]/ig, "_"))
            return pageId.replace(/[^A-Z0-9]/ig, "_");
        },
    }


}
</script>

<style lang="scss" scoped>
$small: 300px;
$medium: 900px;

.v-card--reveal {
    align-items: center;
    bottom: 0;
    justify-content: center;
    opacity: .92;
    position: absolute;
    width: 100%;

    .card-hover {
        position: absolute;
        align-items: center;
        text-align: center;

        h1 {
            font-weight: bold;
            font-size: 1rem !important;
            letter-spacing: 0.15rem;
            line-height: 2.5rem;
        }

        .v-list {
            background: $color_invisible;
            color: $color_main-lightest;

            .v-icon {
                color: $color_main-lightest;
            }

            .card-infoValue {
                display: flex;
                align-items: center;
                justify-content: space-between;
                color: $color_main-lightest;

                p {
                    font-size: .75rem !important;
                    padding: 0.25rem 0rem;
                    margin-bottom: 0;

                    @media screen {
                        @media (max-width: 320px) {
                            font-size: .55rem !important;
                        }
                    }
                }

                span {
                    font-size: .9rem;
                    font-weight: bold;
                    background-color: $color_main;
                    padding: 0.15rem 0.25rem;
                    border-radius: 5px;

                    @media screen {
                        @media (max-width: 320px) {
                            font-size: .75rem !important;
                        }
                    }
                }

            }
        }

        .card-btn {
            background-color: $color-main;
            color: white;
        }
    }
}
</style>