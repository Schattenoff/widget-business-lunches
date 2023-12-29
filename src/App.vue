<template>
  <widget-business-lunches
    title="Бизнес-ланчи в Витебске"
    :lunchList="businessLunchList.data"
  />
</template>

<script>
import WidgetBusinessLunches from "./components/WidgetBusinessLunches/WidgetBusinessLunches.vue";
import businessLunchList from "./mockData/business-lunches.json";

export default {
  components: {
    WidgetBusinessLunches,
  },
  data() {
    return {
      businessLunchList,
    };
  },
};
</script>
