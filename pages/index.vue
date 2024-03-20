<script setup>
const showText = ref(false)
const showConsole = () => console.log("Click")
const showAlert = () => {
    alert("Click")
    showText.value = !showText.value
}
</script>

<template>
    <h3>strona główna</h3>
    <button @click="showAlert">Kliknij mnie</button>
    <button @click="showConsole">Kliknij mnie</button>
    <br/>
    <span v-if="showText">Pokaz text (v-if)</span><br/>
    <span v-show="showText">Pokaz text (v-show)</span>
</template>

<style scoped lang="scss">
h3 {
    span {
        color: green
    }
    
}
</style>