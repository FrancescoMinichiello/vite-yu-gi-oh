<script>
import axios from 'axios'

export default {
  data() {
    return {
      cardsList: [],
      apiUrl: "https://db.ygoprodeck.com/api/v7/cardinfo.php?num=30&offset=0"
    }
  },
  methods: {
    getCards(){
      axios.get(this.apiUrl)
      .then((response)=>{
        console.log(response.data.data);
        this.cardsList = response.data.data;
      })
    }
  },
  created() {
    this.getCards()
  },
}
</script>

<template>
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