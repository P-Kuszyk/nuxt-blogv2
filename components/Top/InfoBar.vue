<script setup>
const props = defineProps(
    {
      title: {
        type: String,
        default: () => 'Domyślna wartość'
      },
      content: {
        type: String,
        default: () => 'Domyślna wartość'
      }
    }
)

const description = ref(0)

const clickbutton = () => description.value = 'Opis'
const clickbutton2 = () => props.title = 'Opis' // ta operacja sie nie wykona bo props jest na modyfikatorze readonly
const clickbutton3 = () => description.value += 1 
</script>
<template>
  <div class="info">
<span>
<slot name="title">Domyślna</slot>:
</span>
    <slot name="content">Domyślna</slot>
  </div>

  <div class="info2">
<span>
<slot name="title2">Domyślna</slot>:
</span>
    <slot name="content2">Domyślna</slot>
  </div>

  <div>
    <h1>{{ title }}</h1>
    <p>{{ content }}</p>
    <p>{{ description }}</p>
  </div>
  <button @click="clickbutton">Klik</button>
  <button @click="clickbutton2">Klik2</button>
  <button @click="clickbutton3">Klik3</button>


</template>

<style scoped lang="scss">
.info, .info2 {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 50px;
  background-color: #B803FF;
  color: #fff;

  span {
    margin-right: 10px;
  }
}
</style>