<template>
  <div class="Home">
    <div class="header">
      <img
        src="https://d3i4yxtzktqr9n.cloudfront.net/web-eats-v2/ee037401cb5d31b23cf780808ee4ec1f.svg"
        alt=""
        srcset=""
      />
      <input type="text" placeholder="Recherche ? " />
    </div>
    <div class="Baniere"></div>
    <RestaurentRow
      v-for="(data, i) in DataRestaurent"
      :key="i"
      :theee_restaurant="data"
    />
  </div>
</template>

<script>
import info from "../BDD/BDD";
import { onMounted, ref } from "vue";
import RestaurentRow from "../components/RestaurentRow.vue";
export default {
  name: "Home",
  components: {
    RestaurentRow,
  },

  setup() {
    class Restaurant {
      constructor(name, note, image, drive_time) {
        this.name = name;
        this.note = note;
        this.image = image;
        this.drive_time = drive_time;
      }
    }
    let DataRestaurent = ref([]);
    const MakeDATAresto = () => {
      let theee_restaurant = [];
      for (const restaurant of info) {
        const new_restaurent = new Restaurant(
          restaurant.name,
          restaurant.note,
          restaurant.image,
          restaurant.drive_time
        );

        if (theee_restaurant.length === 2) {
          theee_restaurant.push(new_restaurent);
          DataRestaurent.value.push(theee_restaurant);
          theee_restaurant[""];
        } else {
          theee_restaurant.push(new_restaurent);
        }
      }
    };
    onMounted(MakeDATAresto);
    return {
      DataRestaurent,
    };
  },
};
</script>

<style>
.header {
  height: 120px;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
img {
  width: 200px;
}
input {
  background-color: beige;
  width: 400px;
  height: 30px;
  outline: none;

  padding-left: 20px;
}
.Baniere {
  height: 200px;
  width: 100%;
}
</style>
