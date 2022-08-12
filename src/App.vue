<template>
  <div id="app">
    <h1>List of Items</h1>
    <input class="input" v-model="item" type="text" placeholder="add item" />
    <button class="button" @click="addTodo">
      <span>Add</span>
    </button>

    <ol v-if="items.length > 0" class="list-items">
      <li class="list-item" v-for="(item, index) in items" :key="index">
        {{ item.name }}
        <button v-on:click="removeItem(index)">
          <span>x</span>
        </button>
      </li>
    </ol>
    <p v-else>Please add items</p>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      item: "",
      items: [
        { name: "item 1" },
        { name: "item 2" },
        { name: "item 3" },
        { name: "item 4" },
      ],
    };
  },
  methods: {
    addTodo() {
      console.log("alert");
      if (this.item.length === 0) {
        alert("please add text");
        return;
      }
      this.items.push({ name: this.item });
    },
    removeItem(index) {
      this.items.splice(index, 1);
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  box-sizing: border-box;
}

.input {
  padding: 0.5em;
  margin-right: 1em;
}

.button {
  padding: 0.5em;
}

.list-item {
  border: 1px solid #000;
  margin: 1em;
  display: flex;
  padding: 0.5em;
  justify-content: space-between;
}
</style>
