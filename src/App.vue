<template>
  <div>
    <header class="hero is-info">
      <div class="hero-body">
        <div class="container">
          <h1 class="title has-text-centered">Grocery List App</h1>
        </div>
      </div>
    </header>

    <ItemInput @onAddItem="handleAddItem"/>
    <ItemList :list="itemList" @onRemoveItem="handleRemoveItem"/>
  </div>
</template>

<script>
import ItemInput from "./components/ItemInput";
import ItemList from "./components/ItemList";

export default {
  name: "app",
  components: {
    ItemInput,
    ItemList
  },
  data() {
    return {
      itemList: []
    };
  },
  methods: {
    handleAddItem(item) {
      this.itemList.push(item);
    },
    handleRemoveItem(item) {
      let index = this.itemList.indexOf(item);
      this.itemList.splice(index, 1);
    }
  }
};
</script>

<style>
</style>
