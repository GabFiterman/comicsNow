<template>
    <div class="SearchBox">
        <div>
            <input class="SearchBox-input" placeholder="Searching for Characters" />
        </div>

        <div class="SearchBox-radioGroup">
            <input v-model="radioGroup" class="SearchTypeRadio" type="radio"  v-for="n in 2" :key="n" :value="n" />
        </div>
    </div>
</template>

<script>

export default {
    name: 'SearchBox',
    data() {
        return {
            radioGroup: 1,
        }
    },
}
</script>

<style lang="scss" scoped>
.SearchBox{
    display: flex;
    flex-direction: row;
    justify-content: end;
    align-items: center;
    width: 100%;
    .SearchBox-input {
        background-color: rgba(50, 0, 0, .55);
        font-size: 0.85rem;
        padding: .65rem 1.25rem;
        outline: none;
        border: none;
        // min-width: 16rem;
        width: 80%;
        border-radius: 2rem;
        color: white;
    
        &:focus {
            background-color: rgba(50, 0, 0, .9);
        }
    
        &::placeholder {
            color: rgba(255, 255, 255, .35);
        }
    }
    .SearchBox-radioGroup{
        display: flex;
    }
}
</style>