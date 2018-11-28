<template>
  <div class="section">
    <div class="container">
      <h1 class="title">Item List</h1>

      <table class="table is-fullwidth is-bordered" v-if="list.length">
        <tbody>
          <tr v-for="item in list" :key="item.text">
            <td @click="toggleCartStatus(item)">
              <span class="icon" :class="[ item.inCart ? 'has-text-info' : 'has-text-danger']">
                <i class="fas fa-check-circle"></i>
              </span>
              {{ item.text }} ({{ item.quantity }})
              <button
                class="button is-danger is-small is-pulled-right"
                @click="removeItem(item)"
              >
                <span class="icon">
                  <i class="far fa-trash-alt"></i>
                </span>
              </button>
            </td>
          </tr>
        </tbody>
      </table>

      <div class="notification is-danger" v-else>There are currently no items in list.</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ItemList",
  props: {
    list: Array
  },
  methods: {
    toggleCartStatus(item) {
      item.inCart = !item.inCart;
    },
    removeItem(item) {
      this.$emit("onRemoveItem", item);
    }
  }
};
</script>

<style scoped>
tr {
  cursor: pointer;
}
</style>

