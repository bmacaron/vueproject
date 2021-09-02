<template>
  <div><button v-on:click="clear">clear</button></div>
</template>

<script>
export default {
    name: 'FooterComponent',
    methods : {
      clear() {
        localStorage.clear();
        this.$emit('clearItem');
      }
    }
}
</script>

<style>

</style>