<template>
  <div id="app">
    <!-- <form method="POST" @submit.prevent="onSubmit">
      <input
        type="text"
        placeholder="Please input note"
        v-model="dataForm.name"
      />
      <button>Submit</button>
    </form> -->

    <ul>
      <li v-for="(item,index) in list" :key="item.id">
        <!-- <span>{{ item.name }}</span> -->
        <item :dataItem="item" :index="index"> </item>
        <!-- <action @handleEdit="onEdit(item)" @handleRemove="onRemove(item)" /> -->
         
      </li>
    </ul>
  </div>
</template>

<script>
import Item from './components/Item.vue';
// import Action from "@/components/Action.vue";

const defaultForm = {
  id: undefined,
  name: "",
};
export default {
  name: "App",
  components: {
    Item
    // Action,
  },
  data() {
    return {
      mode: "ADD",
      dataForm: { ...defaultForm },
      list: [
        {
          // Button Alert
          //    Alert: Click Item {i}
          id: 1,
          name: "Note 1",
          action: ["alert"]
        },
        {
          // Console
          //    Console: Click Item {i}
          id: 2,
          name: "Note 2",
          action: ["console"]
        },
        {
          // Click count
          // Action:
          //    Count so 3 len sau moi lan bam
          id: 3,
          name: "Note 3",
          action: ["count"]
        },
        {
          // Button Alert
          // Console:
          id: 4,
          name: "Note 3",
          action: ["alert", "console"]
        },
      ],
    };
  },
  methods: {
    onSubmit() {
      if (this.dataForm.name.trim()) {
        if (this.mode === "ADD") {
          this.list.push({
            id: Math.round(Math.random() * 1000),
            name: this.dataForm.name,
          });
        } else {
          // console.log("hiih");
          const index = this.list.findIndex(
            (item) => item.id === this.dataForm.id
          );
          this.list[index] = { ...this.dataForm };
        }

        this.onResetForm();
      }
    },
    onEdit(dataItem) {
      this.mode = "EDIT";
      console.log(dataItem);
      this.dataForm = { ...dataItem };
    },
    onRemove(dataItem) {
      const index = this.list.findIndex((item) => item.id === dataItem.id);
      this.list.splice(index, 1);
    },
    onResetForm() {
      this.mode = "ADD";
      this.dataForm = { ...defaultForm };
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}

ul {
  width: 300px;
  padding: 0;
}

li {
  display: flex;
  justify-content: space-between;
}

input {
  margin-right: 4px;
}

button + button {
  margin-left: 4px;
}
</style>