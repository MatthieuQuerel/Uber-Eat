<template>
  <div class="Restaurant-Card">
    <div :style="changeBacground" class="Restaurant-Image">
      <img
        src="https://cn-geo1.uber.com/image-proc/resize/eats/format=webp/width=550/height=440/quality=70/srcb64=aHR0cHM6Ly9kMXJhbHNvZ25qbmczNy5jbG91ZGZyb250Lm5ldC8zNzg4MDJiMC1jNTI4LTQ4MjktYjBiNS0wY2M2NDBkZjYzY2QuanBlZw=="
      />
    </div>
    <div class="Restaurant-Information">
      <div class="top">
        <p class="name">{{ info_Restaurant.name }}</p>
        <span class="note">{{ info_Restaurant.note }}</span>
      </div>
      <div class="bas">
        <p class="Time">{{ info_Restaurant.drive_time }}</p>
        <p class="Prix">€€</p>
      </div>
    </div>
  </div>
</template>

<script>
import { computed } from "vue";
export default {
  name: "RestaurentCard",

  props: {
    info_Restaurant: Object,
  },
  setup(props) {
    const changeBacground = computed(() => {
      return {
        Bacground: "url($(props.info_Restaurant.image))",
      };
    });

    return {
      changeBacground,
    };
  },
};
</script>
<style>
.Restaurant-Card {
  width: 20%;
  height: 10%;
}
.Restaurant-Image {
  height: 18%;
  width: 200px;
  align-items: center;
  background-position: center;
}
.Restaurant-Information {
  margin: 0px 0px;
}
.bas {
  display: flex;
}
.top {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.Time {
  font-size: 18px;
  margin-right: 3px;
}
.name {
  font-size: 21px;
}
.note {
  background-color: gray;
  width: 30px;
  height: 30px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 16px;
  border-radius: 15px;
}
</style>
