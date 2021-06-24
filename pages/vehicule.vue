<template>
    <div class="container-vehicule">
        <Header></Header>
        <div class="vehicule-layout">
            <div class="main-content">
                <img :src="vehicule.pictures[imgToDisplay].url" alt="">
                <div class="vehicule-infos-container">
                    <img :src="vehicule.vehicle_owner_picture_url" alt="">
                    <div class="vehicule-infos">
                        <h1>{{ vehicule.title }}</h1>
                        <p>{{ vehicule.vehicle_location_zipcode }} {{ vehicule.vehicle_location_city }}</p>
                        <p>{{ vehicule.review_count }}</p>
                    </div>
                </div>
                <div class="vehicule-commodités">
                    <div v-for="commodité of commoditées" :key="commodité">
                        <div class="icon-placeholder"></div>
                        <p>{{ commodité }}</p>
                    </div>
                </div>
            </div>
            <div class="left-sidebar">
                <div class="price">
                    <p>A partir de {{ vehicule.starting_price }}€ /j</p>
                </div>
                <div class="reassurance">
                    <p>Reassurance</p>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import Header from '../components/Header.vue'
export default {
    data(){
        return {
            imgToDisplay: 0,
            commoditées : ['4 places avec ceinture', '4 places couchage', '<3500kg Permis B']
        }
    },
    async asyncData({ route, $http }) {
        const query = route.query.id;
        let vehicules = await $http.$get(`https://gitlab.com/api/v4/snippets/2095016/raw`);
        const vehicule = vehicules.results.find(x => x.id == query);
        return { vehicule }
    }
}
</script>


<style>
.container-vehicule {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    width: 100%;
}

.vehicule-layout{
    display: flex;
    flex-wrap: wrap;
    width: 100%;
    max-width: 1200px;
}

.main-content{
    width: 70%;
    padding: 10px;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
}

.main-content>img{
    width: 100%;
    height: 500px;
    object-fit: cover;
}

.main-content .vehicule-infos-container{
    width: 100%;
    padding: 20px 0px;
    display: flex;
    justify-content: flex-start;
    align-items: flex-start;
    /* flex-wrap: wrap; */
}

.main-content .vehicule-infos-container>img{
    float: left;
    width: 150px;
}


.main-content .vehicule-infos-container .vehicule-infos{
    padding: 0px 20px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
}

.main-content .vehicule-infos-container .vehicule-infos>*{
    margin-bottom: 10px;
}

.vehicule-commodités{
    display: flex;
    align-items: flex-start;
    width:100%;
}

.vehicule-commodités>div{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin: 50px 50px 0px 0px;
}

.vehicule-commodités p{
    font-size: 0.6em;
    text-align: center;
}

.icon-placeholder{
    width: 50px;
    height: 50px;
    background-color: rgba(0, 0, 0, 0.1);
    margin-bottom: 10px;
}

.left-sidebar{
    width: 30%;
    padding: 10px;
}

.left-sidebar>div{
    width: 100%;
    border: 1px solid rgba(0, 0, 0, 0.1);
    border-radius: 10px;
    padding: 20px;
    box-sizing: border-box;
}

.left-sidebar .price{
    height: 200px;
    margin-bottom: 20px;
}

.left-sidebar .reassurance{
    height: 500px;
    display: flex;
    justify-content: center;
    align-items: center;
}
</style>