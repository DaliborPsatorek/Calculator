<script setup>
  defineProps(["number"])
</script>

<template>
  <div @click="$emit('numberButtonWasClicked', number )">
    {{ number.name }}
  </div>
</template>

<style scoped>
div{
  background-color: gray;
  color:white;
  font-size: 2rem;
  float: left;
  width: 2rem;
  height: 2rem;
  margin-left: 1rem;
  margin-top: 1rem;
  margin-bottom: 1rem;
  text-align: center;
}
</style>
