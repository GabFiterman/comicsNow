<template>
    <div class="footer">
        <router-link to="/">
            <img class="mt-2" src="../../public/MarvelComics-64px.png"/>
        </router-link>

        <p class="mt-2">developed by: 
            <a href="https://github.com/GabFiterman" target="_blank">
                GabFiterman
            </a>  
            - {{ getCurrentYear() }}
        </p>
    </div>
</template>

<script>
export default {
    name:'Footer',

    data(){
        return {
            logo: '../../public/Comics.png',
        };
    },

    methods: {
        getCurrentYear() {
            return new Date().getFullYear() ;
        }
    }
};
</script>

<style lang="scss" scoped>
.footer{
    background-color: white;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;

    border-top: 6px solid $color-main;
    box-shadow: 0px 12px 18px 0px rgba(0, 0, 0, 0.33) inset;
    height: 22vh;
    

    img{
        max-height: 6rem;
        width: auto;
        
    }

    p{
        color: #afafaf;
        letter-spacing: 0.15rem;
        font-weight: bold;

        a{
            color: $color-main;
            font-weight: 1000;
            border-bottom: 1px solid $color-main;
        }
    }
}
</style>
