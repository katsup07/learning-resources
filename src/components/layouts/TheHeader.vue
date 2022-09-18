<template>
  <header>
    <h1>{{ title }}</h1>
  </header>
</template>

<script>
export default {
  props: ['title'],
}
</script>


<style scoped>
header {
  background: dodgerblue;
  color: rgb(255, 254, 243);
  margin: 0;
  padding: 1rem;
  font-size: 1.4rem;
  font-weight: 700;
  text-align: center;
}
h1{
  margin: 0;
}
</style>