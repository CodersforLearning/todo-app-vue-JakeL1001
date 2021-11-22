<template>
    <button @click="onClick()" :style="{background: color}">
        {{ text }}
    </button> 
</template>

<script>

export default {
    name: 'Button',
    props: {
        text: String,
        color: String
    },
    methods: {
        onClick() {
            this.$emit('button-click')
        }
    }
}
</script>

<style scoped>
button{
    background-color: #262a2b;
    border-radius: 5px;
    align-items: center;
    justify-content: center;
    color: #d2d7db;
    font-size: 1.5em;
    padding: 10px;
    margin: 10px;
}
</style>