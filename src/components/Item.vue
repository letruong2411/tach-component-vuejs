<template>
  <div>
    <span>{{ dataItem.name }}</span>
    <border :dataItem="dataItem" :index="index"/>
  </div>
</template>
<script>
import Border from "./Border.vue";
export default {
  components: { Border },
  name: "Item",
  props: {
    dataItem: {
      type: Object,
      required: false,
      default: () => ({}),
    },
    index: {
      type: Number,
      required: false,
      default: () => 0
    }
  },
  data() {
    return {};
  },
};
</script>