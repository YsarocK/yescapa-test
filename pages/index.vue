<template>
  <div class="container">
    <Header></Header>
    <div class="filter-container">Filter</div>
    <div class="vehicule-list">
      <vehicule-card :vehicule="vehicule" v-for="vehicule of vehicules.results" :key="vehicule.title"></vehicule-card>
    </div>
  </div>
</template>

<script>
import VehiculeCard from '../components/VehiculeCard.vue';
import Header from '../components/Header.vue'

export default {
  components: { VehiculeCard, Header },

  async asyncData({ $http }) {
    let vehicules = await $http.$get(`https://gitlab.com/api/v4/snippets/2095016/raw`);
    return { vehicules }
  }
}
</script>

<style>

.container {
  display: flex;
  flex-wrap: wrap;
  width: 100%;
}

.filter-container{
  width: 200px;
  margin-bottom: 0;
  border: 1px solid rgba(0, 0, 0, 0.1);
  border-radius: 10px;
  margin: 10px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.vehicule-list{
  display: flex;
  justify-content: flex-start;
  flex-wrap: wrap;
  align-items: flex-start;
  width: 100%;
  max-width: 1200px;
}

</style>
