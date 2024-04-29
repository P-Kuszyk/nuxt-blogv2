<template>
    <div class="dinner">
      <h1>{{ title }}</h1>
      <img class="card" :src="img" />
      <h3>Ocena klientów {{ opinion }}/5</h3>
      <h5>{{ comment }}</h5>
    </div>
  </template>
  
  <script>
  export default {
    name: 'DinnerComponent',
    props: {
      id: {
        type: Number,
        default: () => Math.floor(Math.random() * 1000), // Losowe id
      },
      title: {
        type: String,
        default: () => "Danie dnia", // Domyślny tytuł
      },
      img: {
        type: String,
        default: () => "https://placekitten.com/200/300", // Domyślny obrazek (kotek)
      },
      opinion: {
        type: Number,
        default: () => Math.floor(Math.random() * 5) + 1, // Losowa ocena od 1 do 5
      },
      comment: {
        type: String,
        default: () => "Brak komentarza", // Domyślny komentarz
      }
    }
  }
  </script>
  