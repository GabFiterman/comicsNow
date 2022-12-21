<template>
    <div class="CustomEvents">
        <h1>TESTING PAGE</h1>
        <p>CustomEvents Counter: {{  localCounter }}</p>
        <parent @count="(i) => localCounter = i"/>
    </div>
</template>

<script>
import parent from '../components/Test/parent.vue';

export default {
    name: 'CustomEvents',
    components: {
        parent
    },
    data() {
        return {
            localCounter: 0,
        }
    }
}
</script>

<style lang="scss" scoped>
.CustomEvents {
    background-color: black;
    padding: 2rem 3rem;
}
</style>