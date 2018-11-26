<template>
  <div>
    <ItemInput @onAddItem="handleAddItem" />
  </div>
</template>

<script>
import ItemInput from './components/ItemInput';

export default {
  name: 'app',
  components: {
    ItemInput
  },
  data() {
    return {
      itemList: []
    };
  },
  methods: {
    handleAddItem(item) {
      this.itemList.push(item);
    }
  }
};
</script>

<style>
</style>
