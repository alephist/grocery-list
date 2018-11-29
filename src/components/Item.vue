<template>
  <tr>
    <td @click="toggleCartStatus">
      <span class="icon" :class="[ item.inCart ? 'has-text-info' : 'has-text-danger']">
        <i class="fas fa-check-circle"></i>
      </span>
      {{ item.text }} ({{ item.quantity }})
      <button
        class="button is-danger is-small is-pulled-right"
        @click="removeItem"
      >
        <span class="icon">
          <i class="far fa-trash-alt"></i>
        </span>
      </button>
    </td>
  </tr>
</template>

<script>
export default {
  name: "Item",
  props: ["item"],
  methods: {
    toggleCartStatus() {
      this.$emit("onToggleCartStatus", this.item);
    },
    removeItem() {
      this.$emit("onRemoveItem", this.item);
    }
  }
};
</script>

<style scoped>
tr {
  cursor: pointer;
}
</style>
