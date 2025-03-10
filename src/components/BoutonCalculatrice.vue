<template>
  <button @click="$emit('send-value', value)">{{ value }}</button>
</template>

<script>
export default {
  props: ['value']
};
</script>

<style scoped>
button {
  padding: 15px;
  font-size: 18px;
  font-weight: bold;
  border: none;
  border-radius: 8px;
  background-color: #ff99cc;
  color: white;
  cursor: pointer;
  transition: all 0.3s ease;
  box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
}

button:hover {
  background-color: #66ff99;
  transform: scale(1.05);
}

button:active {
  transform: scale(0.95);
  box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.2);
}
</style>