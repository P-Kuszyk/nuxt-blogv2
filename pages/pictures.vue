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
    margin-top: 25px;
    border-radius: 20px; 
    
  }
  img:first-child{
    margin-left: 100px;
    transition-timing-function: ease-in;
    transition-delay: 2s;
  }
  img:nth-of-type(2){
    margin-left: 250px;
  }
  img:nth-of-type(3){
    margin-left: 450px;
  }
}
</style>

