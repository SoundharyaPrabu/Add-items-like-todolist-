
<template>
  <div id="app">
    <AddItem />
  </div>
</template>

<script>
import AddItem from './components/AddItem.vue'; // ✅ corrected path

export default {
  components: {
    AddItem
  }
};
</script>

<style>
#app {
  font-family: Arial, sans-serif;
  padding: 40px;
  background-color: #f3f3f3;
}
</style>
