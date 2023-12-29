<template>
  <div class="lunch-card">
    <a :href="lunch.link" class="lunch-card__img-wrapper" target="_blank">
      <span class="lunch-card__easy-opacity" />
      <img class="lunch-card__img" :src="lunch.image" />
      <div class="lunch-card__about">
        <span class="lunch-card__about-name">
          {{ lunch.name }}
        </span>
        <span class="lunch-card__about-address">
          {{ lunch.address }}
        </span>
        <span
          class="lunch-card__about-time"
          v-if="lunch.startTime || lunch.endTime"
        >
          {{ `${lunch.startTime} - ${lunch.endTime}` }}
        </span>
      </div>
    </a>

    <ul class="lunch-card__menu">
      <li
        class="lunch-card__menu-item"
        v-for="(item, index) in lunch.menu"
        :key="index"
      >
        {{ item.name }}
        <span
          title="Стоимость блюда"
          class="lunch-card__menu-item__price"
          v-if="item.price"
          >{{ item.price.toFixed(2) }}
        </span>
      </li>
    </ul>
    <div class="lunch-card__total-price">
      {{ lunch.totalPrice.toFixed(2) }} р
    </div>
  </div>
</template>

<script>
export default {
  props: {
    lunch: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style scoped>
.lunch-card {
  position: relative;
  min-width: calc(100% / 4);
  padding-bottom: 40px;
  white-space: normal;
}

.lunch-card__img-wrapper {
  position: relative;
  display: inherit;
  height: 150px;
}

.lunch-card__img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.lunch-card__easy-opacity {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(
      to bottom,
      rgba(100, 61, 15, 1) 0,
      rgba(100, 61, 15, 0) 100%
    )
    repeat scroll 0 0;
  opacity: 0.4;
  transition: opacity 0.3s ease;
}

.lunch-card__easy-opacity:hover {
  opacity: 0.5;
}

.lunch-card__about {
  position: absolute;
  top: 15px;
  left: 23px;
  color: #fff;
  display: flex;
  flex-direction: column;
  gap: 8px;
}
.lunch-card__about-name {
  font: 700 21px/23px "Roboto Condensed";
  text-shadow: 0 1px 0 rgba(0, 0, 0, 0.35);
}

.lunch-card__about-name:hover {
  text-decoration: underline;
}

.lunch-card__about-address {
  font: 300 15px/16px Roboto;
  text-shadow: 0 1px 0 rgba(0, 0, 0, 0.2);
  white-space: nowrap;
  text-overflow: ellipsis;
  overflow: hidden;
  max-width: 270px;
  position: relative;
  display: block;
}

.lunch-card__about-address:hover {
  text-decoration: underline;
}

.lunch-card__about-time {
  font: 13px/13px Roboto;
  position: relative;
  display: block;
  text-shadow: 0 1px 0 rgba(0, 0, 0, 0.2);
}

.lunch-card__menu {
  padding: 12px 35px 13px 23px;
  display: flex;
  flex-direction: column;
  gap: 13px;
}

.lunch-card__menu-item {
  list-style-type: none;
  font: 300 17px/22px Roboto;
  padding: 2px 0;
}

.lunch-card__menu-item__price {
  font: 11px/16px "Open sans";
  display: inline-block;
  margin: 4px 0 0 7px;
  background: #c3b8a5;
  padding: 0 3px;
  border-radius: 2px;
  vertical-align: baseline;
  position: absolute;
  cursor: default;
}

.lunch-card__total-price {
  font: 900 24px/29px Roboto;
  margin: 5px 0 0 19px;
  padding: 0 5px;
  border-radius: 2px;
  display: inline-block;
  color: #000;
  transition: background-color 0.3s ease;
}

.lunch-card:hover .lunch-card__total-price {
  background-color: #ff0000;
  color: #fff;
}
</style>
