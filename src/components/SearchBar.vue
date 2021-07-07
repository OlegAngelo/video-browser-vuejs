<template>
    <div class="container">
        <input @keyup.enter="onChange" />
    </div> 
</template>

<script>
export default {
    name:'SearchBar',
    methods:{
        onChange(event) {
            this.$emit('termChange', event.target.value);
        }
    }
}
</script>

<style scoped>
    input{
        width: 75%;
    }

    div{
        text-align: center;
        margin: 20px;
    }
</style>