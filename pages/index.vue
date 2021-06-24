<template>
  <div class="container">
     <div v-for="vehicule of vehicules.results" :key="vehicule.title">
       <vehicule-card :vehicule="vehicule"></vehicule-card>
     </div>
  </div>
</template>

<script>
import VehiculeCard from '../components/VehiculeCard.vue';
export default {
  components: { VehiculeCard },
    async asyncData({ $http }) {
      let vehicules = await $http.$get(`https://gitlab.com/api/v4/snippets/2095016/raw`);
      return { vehicules }
    }
}
</script>

<style>
.container {
  display: flex;
  justify-content: center;
}
</style>
