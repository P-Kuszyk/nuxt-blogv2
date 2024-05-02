<script setup>

</script>
<template>
 <div class="background">
 <h3>API</h3>
 <h3>NASA</h3>
 <h3>⭐⭐⭐⭐⭐</h3>
 </div>
</template>
<style scoped lang="scss">
  .background {
    display: flex;
    align-items: center;
    justify-content: flex-start;
    flex-direction: column;
    height: 100%;
    background-color: #131313;
    height: 100vh;
    
    h3{
        font-size: 200px;
        color: gold;
        animation: neon 10s infinite alternate;
    }

    @keyframes neon{
      0% {
        opacity: 1;
      }
      10% {
        opacity: 0.5;
      }
      20% {
        opacity: 0.8;
      }
      30% {
        opacity: 0.2;
      }
      45% {
        opacity: 0.4;
      }
      65% {
        opacity: 0.9;
      }
      65.1% {
        opacity: 0.3;
      }
      75% {
        opacity: 1;
      }
      100% {
        opacity: 0.6;
      }
    }
  }
</style>