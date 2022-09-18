<template>
  <section>
    <the-header title="Learning Resources"></the-header>
    <the-resources></the-resources>
  </section>
</template>

<script>
import TheHeader from './components/layouts/TheHeader.vue';
import TheResources from './components/learning-resources/TheResources.vue';


export default{
  components:{
    TheHeader,
    TheResources,
  },
};
</script>

<style>
*{
  box-sizing: border-box;
}

html {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}

body {
  margin: 0;
}

</style>
