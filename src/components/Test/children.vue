<template>
    <div>
        <h1>Children</h1>
        <p>ChildrenCounter: {{ counter }}</p>

        <div class="test-buttonGroup">
            <button @click="counterMore" class="test-button">Counter++</button>
            <button @click="counterLess" class="test-button">Counter--</button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'children',
    data() {
        return {
            counter: 0,
        };
    },
    methods: {
        counterMore() {
            this.counter++;
            this.emitCounter(this.counter);
        },

        counterLess() {
            this.counter--;
            this.emitCounter(this.counter);
        },

        emitCounter(counter) {
            this.$emit('count', counter);
        },
    },
}
</script>

<style lang="scss" scoped>
.test-buttonGroup{
    display: flex;
    flex-direction: column;
    justify-content: center;
}
</style>