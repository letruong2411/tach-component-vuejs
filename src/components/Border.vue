<template>
  <div style="border: 1px solid red">
    <div v-for="(button, index) in dataItem.action" :key="index">
      <button @click="onClick">{{ button }}</button>
    </div>
  </div>
</template>
<script>
export default {
  name: "Border",
  props: {
    dataItem: {
      type: Object,
      required: false,
      default: () => ({}),
    },
    index: {
      type: Number,
      required: false,
      default: () => 0,
    },
  },
  data() {
    return {
       count3: 0
    }
  },
  methods: {
    onClick(e) {
      // console.log(e.target.textContent);
      const value = e.target.textContent;
      if (value === "alert") {
        return alert(`item: ${this.index}`);
      } else if (value === "console") {
        return console.log(`item thu ${this.index}`);
      } else {
        return console.log(`count= ${this.count3++}`);
      }
    },
  },
};
</script>