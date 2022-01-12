<template>
    <header>
        <input v-model="userSearch" type="text">
        <button @click="$emit('passSearch', userSearch)">search</button>
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