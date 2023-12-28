<template>
  <div>
    <div>Hello, world!</div>
    <div v-for="(lunch, index) in businessLunchList.data" :key="index">
      <h1>{{ lunch.name }}</h1>
    </div>
  </div>
</template>

<script>
import businessLunchList from "./mockData/business-lunches.json";

export default {
  data() {
    return {
      businessLunchList,
    };
  },
};
</script>
