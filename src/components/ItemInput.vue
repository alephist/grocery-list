<template>
  <div class="column is-6">
    <h1 class="title">Add New Item</h1>

    <div class="field">
      <label for="name" class="label">Name:</label>
      <div class="control">
        <input type="text" class="input" id="name" v-model="itemName">
      </div>
    </div>

    <div class="field">
      <label for="quantity" class="label">Quantity:</label>
      <div class="control">
        <input type="number" class="input" id="quantity" v-model.number="itemQuantity">
      </div>
    </div>

    <div class="field">
      <div class="control">
        <button class="button is-link" @click="addItem">Add Item</button>
      </div>
    </div>
  </div>
</template>

<script>
const uuidv4 = require('uuid/v4');

export default {
  name: "ItemInput",
  data() {
    return {
      itemName: "",
      itemQuantity: null
    };
  },
  methods: {
    addItem() {
      if (this.itemName && this.itemQuantity) {
        let item = {
          id: uuidv4(),
          text: this.itemName,
          quantity: this.itemQuantity,
          inCart: false
        };

        this.$emit("onAddItem", item);

        this.itemName = "";
        this.itemQuantity = null;
      }
    }
  }
};
</script>

<style>
</style>
