<template>
  <div class="vehicule-card-container">
    <p>{{ this.vehicule.title}}</p>
  </div>
</template>

<script>
export default {
   name: 'vehicule-card',
   props: ['vehicule'],
}
</script>

<style>
.vehicule-card-container{
  display: flex;
  flex-direction: column;
  justify-content: center;
}
</style>
