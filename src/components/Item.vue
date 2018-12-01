<template>
  <tr>
    <td>
      <button
        class="check-icon button is-small"
        :class="[ item.inCart ? 'is-info' : 'is-danger']"
        @click="toggleCartStatus"
      >
        <span class="icon">
          <i class="fas fa-check fa-lg"></i>
        </span>
      </button>
      {{ item.text }} ({{ item.quantity }})
      <div class="field is-grouped is-pulled-right">
        <div class="control">
          <button class="button is-info is-small" @click="incrementQuantity">
            <span class="icon">
              <i class="fas fa-plus"></i>
            </span>
          </button>
        </div>

        <div class="control">
          <button class="button is-info is-small" @click="decrementQuantity">
            <span class="icon">
              <i class="fas fa-minus"></i>
            </span>
          </button>
        </div>

        <div class="control">
          <button class="button is-danger is-small" @click="removeItem">
            <span class="icon">
              <i class="far fa-trash-alt"></i>
            </span>
          </button>
        </div>
      </div>
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
    },
    incrementQuantity() {
      this.$emit("onIncrementQuantity", this.item);
    },
    decrementQuantity() {
      this.$emit("onDecrementQuantity", this.item);
    }
  }
};
</script>

<style scoped>
.check-icon {
  border-radius: 50%;
  margin-right: 0.625rem;
}
</style>
