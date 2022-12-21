<template>
    <div>
        <h1>Parent</h1>
        <p>ParentCounter: {{ localCounter }}</p>
        <children @count="(i) => { 
            localCounter = i; 
            this.$emit('count', i);
        }"/>
    </div>
</template>

<script>
import children from './children.vue';
export default {
    name: 'parent',

    components: { children },

    data() {
        return {
            localCounter: 0,
        }
    }
    
}
</script>

<style>

</style>