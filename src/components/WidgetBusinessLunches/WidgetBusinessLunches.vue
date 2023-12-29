<template>
  <div class="widget-business-lunches">
    <div class="widget-business-lunches__header">
      <h2 class="widget-business-lunches__title">
        <a href="https://carte.by/vitebsk/" target="_blank">{{ title }}</a>
      </h2>
      <a href="https://carte.by/vitebsk/" target="_blank">
        <div class="widget-business-lunches__carte-icon" />
      </a>
      <div class="widget-business-lunches__actions">
        <span
          class="widget-business-lunches__actions-arrow left"
          :class="{ inactive: atStart }"
          @click="prev"
        />
        <span
          class="widget-business-lunches__actions-arrow right"
          :class="{ inactive: atEnd }"
          @click="next"
        />
      </div>
    </div>
    <div
      class="widget-business-lunches__list"
      :style="{ transform: `translateX(-${currentIndex * 25}%)` }"
    >
      <lunch-card
        v-for="(lunch, index) in lunchList"
        :key="index"
        :lunch="lunch"
      />
    </div>
  </div>
</template>

<script>
import LunchCard from "./LunchCard/LunchCard.vue";
export default {
  components: { LunchCard },
  props: {
    title: {
      type: String,
      required: true,
    },
    lunchList: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      currentIndex: 0,
    };
  },
  computed: {
    atStart() {
      return this.currentIndex === 0;
    },
    atEnd() {
      return this.currentIndex >= this.lunchList.length - 4;
    },
  },
  methods: {
    next() {
      if (!this.atEnd) {
        this.currentIndex++;
      }
    },
    prev() {
      if (!this.atStart) {
        this.currentIndex--;
      }
    },
  },
};
</script>

<style scoped>
.widget-business-lunches {
  margin: 40px 0;
  background: url("/img/footer-bg.svg"),
    linear-gradient(to bottom, #eeecda 0, #f4dfc6 100%);
  background-repeat: repeat-x, repeat;
  background-position: 0 114%, 0 0;
  border-top: 1px solid #ddd;
  border-bottom: 1px solid #ddd;
  overflow: hidden;
}

.widget-business-lunches__header {
  padding: 22px 34px 28px 18px;
  display: flex;
  align-items: center;
  gap: 85px;
}

.widget-business-lunches__title a {
  font: 900 60px/60px Roboto;
  letter-spacing: -1px;
  color: #000;
}

.widget-business-lunches__title a:hover {
  text-decoration: underline;
}

.widget-business-lunches__carte-icon {
  background-image: url("/img/carte.svg");
  background-repeat: no-repeat;
  width: 80px;
  height: 39px;
}

.widget-business-lunches__actions {
  margin-left: auto;
  width: 176px;
  display: flex;
  align-items: center;
  justify-content: end;
  gap: 42px;
}

.widget-business-lunches__actions-arrow {
  display: inline-block;
  padding: 20px 21px;
  cursor: pointer;
  opacity: 0.8;
}

.widget-business-lunches__actions-arrow.left {
  background: url("/img/left.svg") no-repeat 50% 50%;
}
.widget-business-lunches__actions-arrow.right {
  background: url("/img/right.svg") no-repeat 50% 50%;
}
.widget-business-lunches__actions-arrow.inactive {
  opacity: 0.1;
  cursor: default;
}

.widget-business-lunches__list {
  display: flex;
  flex-wrap: nowrap;
  gap: 1px;
  transition: transform 0.3s ease;
}
</style>
