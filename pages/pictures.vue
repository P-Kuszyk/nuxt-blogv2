<template>
    <div class="SpacePicture">
      <img class="card" :src="img" />
    </div>
  </template>
  
  <script>
  export default {
    name: 'Picture',
    props: {
      id: {
        type: Number,
      },
      img: {
        type: String,
        reqiured: true,
      },
    }
  }
  </script>
  