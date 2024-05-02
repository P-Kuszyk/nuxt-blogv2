<script setup>
const searchQuery = ref("star")
const resultQuery = ref(null)
const arrayData = ref(null)
const loader = ref(false)
const searchData = async() => {
    loader.value = true
    await useFetch('https://images-api.nasa.gov/search?q=' + searchQuery.value).then((response) => {
        if(response.data) {
            setTimeout(() => {
                resultQuery.value = response.data.value.collection.items
                loader.value = false
                console.log(response.data.value.collection)
            }, 10000)
        }
    }) 
}

onBeforeMount(async () => {
    await searchData()
});

// Użycie watch do obserwacji resultQuery
watch(resultQuery, (newValue, oldValue) => {
    arrayData.value = newValue

    console.log(newValue); // Wyświetla nową wartość resultQuery.value
    // Możesz tutaj dodać dodatkowe logikę, która ma się wykonać po zmianie wartości
}, {
    deep: true // opcja 'deep' jest przydatna, jeśli obserwowany obiekt jest złożony (np. obiekt lub tablica)
});
</script>
<template>
    <div>
        <input type="text" v-model="searchQuery">
        <button @click="searchData" v-if="!loader">Wyszukaj</button>
        <button @click="searchData" disabled v-else>Wyszukaj</button>
        <div class="loading" v-if="loader"><h4>Ładowanie obrazów...</h4></div>

        <div class="result" v-else>
            <div v-for="(value, index) in arrayData" :key="index">
                <template v-if="value.links">
                    <template v-if="value.links[0]">
                        <img :src="value.links[0].href" alt="NASA Image">
                    </template>
                </template>
            </div>
        </div>
    </div>
</template>

<style scoped lang="scss">
button, input{
    border-radius: 5px;
    font-size: 28px;
    margin-top: 10px;
    margin-left: 5px;
    margin-bottom: 3px;
    padding: 2px;
    align: right;
}

input{
    width:400px;
    transition: 0.5s;

    &:hover{
        color: white;
        background: black;
    }

    &:focus{
        color: gold;
        font-style: bold;
    }

}

button{
    width: 150px;
    transition: 0.5s;

    &:hover{
        color: white;
        background: black;
    }

    &:active{
        color: white;
        background-color: red; 
    }
}
img{
    width: 500px;
    height: 250px;
    display: flex;
    margin-top: 5px;
    margin-left: auto;
    margin-right: auto;
}

h4{
    font-size: 30px;
}
</style>