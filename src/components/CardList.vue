<script>
import axios from 'axios'
import MainSearchArchetype from './MainSearchArchetype.vue';

export default {
  data() {
    return {
      cardsList: [],
      apiUrl: "https://db.ygoprodeck.com/api/v7/cardinfo.php?num=30&offset=0",
      archetypesList: [],
      selectedArchetype: ''
    }
  },
  components:{
    MainSearchArchetype
  },
  methods: {
    getCards(archetype = '') {
  let url = this.apiUrl;
  if (archetype) {
    url = `https://db.ygoprodeck.com/api/v7/cardinfo.php?archetype=${archetype}`;
  }
  axios.get(url)
    .then((response) => {
      this.cardsList = response.data.data;
    })
 },
  getArchetypes() {
    axios.get('https://db.ygoprodeck.com/api/v7/archetypes.php')
      .then((response) => {
        this.archetypesList = response.data;
      })
   },
   onArchetypeChanged(archetype) {
   this.selectedArchetype = archetype;
   this.getCards(archetype);
   },
 },
  created() {
    this.getArchetypes();
    this.getCards()
  },
}
</script>

<template>
  <MainSearchArchetype
      :archetypesList="archetypesList"
      @archetype-changed="onArchetypeChanged"
    />
  <div class="card p-2" style="width: 14rem;" v-for="card in cardsList" :key="card.id">
  <img :src="card.card_images[0].image_url" class="card-img-top" :alt="card.name">
  <div class="card-body">
    <h5 class="card-title mb-4">{{ card.name }}</h5>
  </div>
  <p class="fs-4 d-flex justify-content-center">{{ card.archetype }}</p>
  <p class="card-text">cardmarket price {{ card.card_prices[0].cardmarket_price }} € </p>
</div>
</template>

<style lang="scss" scoped>
@use 'bootstrap/scss/bootstrap.scss' as *;
.card-text{
  background-color: white;
  padding: 5px 10px;
  border-radius: 5px;
}
.card{
  background-color: #C18236;
  border-radius: 5px;
}
</style>