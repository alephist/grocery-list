<template>
  <div class="column is-6">
    <h1 class="title">Item List</h1>

    <table class="table is-fullwidth is-bordered" v-if="list.length">
      <tbody>
        <Item
          v-for="item in list"
          :key="item.text"
          :item="item"
          @onToggleCartStatus="toggleCartStatus"
          @onRemoveItem="removeItem"
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
    }
  }
};
</script>

<style>
</style>

