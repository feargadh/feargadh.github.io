<template>
  <div id="Card">
    <toggle :size="4">Good</toggle>
    <toggle :size="4">Cheap</toggle>
    <toggle :size="4">Fast</toggle>
  </div>
</template>

<script>
import Toggle from "./subComponents/Ios-toggle.vue";
export default {
  name: "Card",
  components: {
    Toggle
  }
};
</script>

<style>
#Card {
  font-family: Helvetica, Arial, sans-serif;
  box-shadow: -8px -8px 16px -10px rgba(0, 0, 0, 1),
    8px 8px 16px -10px rgba(255, 255, 255, -15);
  padding: 24px;
  border-radius: 20px;
  background-color: rgba(15, 15, 15, 1);
  width: 600px;
  height: 500px;
  display: flex;
  flex-direction: column;
}
</style>