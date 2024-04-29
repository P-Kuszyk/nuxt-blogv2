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
        this.img = response.data[0].img;
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
  <div class="SpacePicture">
    <img class="card" :src="img" />
  </div>
</template>
