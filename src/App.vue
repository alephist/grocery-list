<template>
  <div>
    <header class="hero is-info">
      <div class="hero-body">
        <div class="container">
          <h1 class="title has-text-centered">Grocery List App</h1>
        </div>
      </div>
    </header>

    <div class="section">
      <div class="container">
        <div class="columns is-variable is-6">
          <ItemInput @onAddItem="handleAddItem"/>
          <ItemList
            :list="itemList"
            @onRemoveItem="handleRemoveItem"
            @onToggleCartStatus="handleToggleCartStatus"
            @onIncrementQuantity="handleIncrementQuantity"
            @onDecrementQuantity="handleDecrementQuantity"
          />
        </div>
      </div>
    </div>
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
      this.saveItems(this.itemList);
    },
    handleRemoveItem(item) {
      let index = this.itemList.indexOf(item);
      this.itemList.splice(index, 1);
      this.saveItems(this.itemList);
    },
    handleToggleCartStatus(item) {
      item.inCart = !item.inCart;
      this.saveItems(this.itemList);
    },
    handleIncrementQuantity(item) {
      item.quantity++;
      this.saveItems(this.itemList);
    },
    handleDecrementQuantity(item) {
      item.quantity === 0 ? (item.quantity = 0) : item.quantity--;
      this.saveItems(this.itemList);
    },
    saveItems(list) {
      localStorage.setItem("items", JSON.stringify(list));
    }
  },
  created() {
    this.itemList = localStorage.getItem("items")
      ? JSON.parse(localStorage.getItem("items"))
      : [];
  }
};
</script>

<style>
</style>
