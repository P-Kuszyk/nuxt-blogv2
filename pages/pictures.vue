<script>
import axios from 'axios';

export default {
  name: 'Picture',
  data() {
    return {
      img: '' 
    };
  },
  mounted() {

    this.fetchData();
  },
  methods: {
    fetchData() {

      axios.get('http://localhost:8000/Picture')
  .then(response => {
    if (response.data && response.data.length > 0) {
      const imgArray = [];
      response.data.forEach(item => {
        imgArray.push(item.img);
      });
      this.img = imgArray;
    } else {
      console.error('Odpowiedź serwera jest pusta.');
    }
  })
  .catch(error => {
    console.error('Błąd pobierania danych:', error);
  });
    }
  }
}
</script>

<template>
  <template>
    <div class="SpacePicture">
      <img v-for="imageUrl in img" 
      :key="imageUrl" class="card" 
      :src="imageUrl" />
    </div>
  </template>  
</template>

<style scoped lang="scss">
.SpacePicture{
  background: black;
  display: flexbox;

  img{
    width: 1300px;
    height: 700px;
    border-radius: 20px; 
    margin-left: auto;
    margin-right: auto;
    display: flex;
    margin-bottom: 10px;
    animation: przesuwanie 15s infinite alternate;
    
    &:nth-of-type(2){
      animation: przesuwanie 12s infinite alternate;
    }

    &:nth-of-type(3){
      animation: przesuwanie 9s infinite alternate;
    }
  }

  @keyframes przesuwanie{
  0%{
      transform: translateX(0);
  }
  50%{
    transform: translateX(25%)
  }
  100% {
      transform: translateX(-25%); 
    }
  }
}
</style>

