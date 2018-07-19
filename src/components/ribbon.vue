<template>
  <div>
    <a :href="profile"><img style="position: absolute; top: 0; left: 0; border: 0;" src="@/assets/forkme.png" alt="Fork me on GitHub"></a>
  </div>
</template>

<script>
export default {
  name: "ribbon",
   data() {
    return {
    }
  },
  props:['profile']
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
