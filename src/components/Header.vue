<template>
    <header>
        <h1>BOOLFLIX</h1>
        <div class="search">
            <input v-model="userSearch" type="text">
            <button @click="$emit('passSearch', userSearch)">search</button>
        </div>
    </header>
</template>

<script>
export default {
    name: 'Header',

    data: function(){
        return{
            userSearch: ''
        }
    }
}
</script>

<style lang="scss" scoped>
header{
    height: 100px;
    width: 100%;
    background: black;
    display: flex;
    justify-content: space-between;
    align-items: center;
    h1{
        color: red;
        display: inline-block;
        margin-left: 20px;
    }
    .search{
        display: flex;
        align-items: center;
        margin-right: 20px;
    }
}
</style>