<template>
  <div class="column is-6">
    <h1 class="title">Item List</h1>

    <table class="table is-fullwidth is-bordered" v-if="list.length">
      <tbody>
        <Item
          v-for="item in list"
          :key="item.id"
          :item="item"
          @onToggleCartStatus="toggleCartStatus"
          @onRemoveItem="removeItem"
          @onIncrementQuantity="incrementQuantity"
          @onDecrementQuantity="decrementQuantity"
        />
      </tbody>
    </table>

    <div class="notification is-danger" v-else>There are currently no items in list.</div>
  </div>
</template>

<script>
import Item from "./Item";

export default {
  name: "ItemList",
  props: {
    list: Array
  },
  components: {
    Item
  },
  methods: {
    toggleCartStatus(item) {
      this.$emit("onToggleCartStatus", item);
    },
    removeItem(item) {
      this.$emit("onRemoveItem", item);
    },
    incrementQuantity(item) {
      this.$emit("onIncrementQuantity", item);
    },
    decrementQuantity(item) {
      this.$emit("onDecrementQuantity", item);
    }
  }
};
</script>

<style>
</style>

