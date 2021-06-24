<template>
  <NuxtLink class="vehicule-card-container" :to="`/vehicule?id=` + this.vehicule.id">
    <img class="vehicule-card-img" :src="this.vehicule.pictures[0].url">
    <div class="vehicule-card-infos">
      <div class="card-header">
        <p class="vehicule-title">{{ this.vehicule.title}}</p>
        <p class="vehicule-starting_price">{{ this.vehicule.starting_price}}€/j</p>
        <p>{{ this.vehicule.vehicle_location_city}}</p>
      </div>
      <div class="card-footer">
        <p class="vehicule-title">{{ this.vehicule.vehicle_seats}} Places • {{ this.vehicule.vehicle_beds}} Couchages</p>
        <div class="vehicule-stars">
          <!-- TODO -->
        </div>
      </div>  
    </div>
  </NuxtLink>
</template>

<script>
export default {
   name: 'vehicule-card',
   props: ['vehicule'],
}
</script>

<style>
.vehicule-card-container{
  text-decoration: none;
  color: black;
  display: flex;
  flex-direction: column;
  justify-content: center;
  width: 30%;
  height: 280px;
  margin: 10px;
  border: 1px solid rgba(0, 0, 0, 0.1);
  border-radius: 10px;
  overflow: hidden;
}

.vehicule-card-img{
  width: 100%;
  height: 50%;
  object-fit: cover;
}

.vehicule-card-infos{
  height: 50%;
  padding: 10px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.vehicule-title{
  width: 70%;
}

.vehicule-starting_price{
  text-align: right;
  width: 20%;
}

.vehicule-card-infos>div{
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
}

.vehicule-card-infos p{
  font-size: 0.9em;
  margin-bottom: 5px;
}
</style>
