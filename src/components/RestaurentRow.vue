<script>
import RestaurentCard from "./RestaurentCard.vue";

export default {
  name: "RestaurentRow",
  components: {
    RestaurentCard,
  },
  props: {
    theee_restaurant: Array,
  },
};
</script>

<template>
  <div class="RestaurentRaw">
    <h2 class="title">Notre Carte</h2>
    <div class="Restaurent">
      <RestaurentCard
        v-for="(card, index) in theee_restaurant"
        :info_Restaurant="card"
        :key="index"
      />
    </div>
  </div>
</template>

<style>
.Restaurent {
  display: flex;
  align-items: center;

  justify-content: space-between;
}
</style>
