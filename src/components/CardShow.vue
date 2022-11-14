<template>
    <div class="card-group">
        <v-card v-for="(res, index) in API_responses" :key="index" width="45vw" class="mx-1 my-2">
            <v-card-text v-text="getName(res.name)"  class="cardTitle"></v-card-text>
            <v-img :src="getImage(index)" height="75vh">
            </v-img>
        </v-card>
    </div>
</template>

<script>
export default {
    name: 'CardShow',

    props: {
        API_responses: Array
    },

    methods: {
        getImage(arr) {
            let imageUrl = `${this.API_responses[arr].thumbnail.path}.${this.API_responses[arr].thumbnail.extension}`
            return imageUrl;
        },
        getName(name) {
            let splited = name.split(new RegExp(/(\().+/g));

            if(splited[0].length >=20){
                let substring = `${splited[0].substring(0, 12)}...`
                return substring;
            }

            return splited[0];
        }
    }


}
</script>

<style lang="scss" scoped>
$THISborder-radius: 10px;

.card-group {
    // margin: 0 2vw;
    padding: 0;
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: center;

    .cardTitle{
        display: flex;
        align-items: center;
        height: 4rem;
        
        background-color: $color-main-darkest;
        color: $color-main-lightest;
        border-bottom: 2px solid white ;
        
        font-family: $font-family_titles;
        font-size: 1.355rem;
        font-weight: bold;
    }
}
</style>