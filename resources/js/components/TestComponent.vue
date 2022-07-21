<template>
  This is a Test Comp

  <button type="buttton" class="btn btn-primary" @click="count()">Click</button>
</template>

<script>
export default {
  setup() {
    function count() {
      const i = 1;
      i++;
      console.log(i);
    }
  },
};
</script>

<style>
</style>