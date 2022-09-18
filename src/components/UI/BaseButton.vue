<template>
  <button  :class="mode"><slot></slot></button>

</template>

<script>
export default{
  props: ['type', 'mode'],
}
</script>

<style scoped>
button {
  font-size: 0.5rem;
  font-family: inherit;
  border: 0;
  padding: 0.1rem 0.4rem;
  background: rgb(187, 187, 187);
  border-radius: 1rem;
  transition: background 0.25s;
  cursor: pointer;
}

button:hover, button:active {
  background: rgb(136, 197, 228);
  color: white;
  border: 0;
}

.danger{
  background: none;
  border: 0.1px solid rgb(187, 187, 187);
  color: rgb(168, 168, 168);
}
.danger:hover{
  background: rgb(255, 70, 70);
  border: 0.1px solid rgb(187, 187, 187);
  color: rgb(255, 255, 255);
}

.highlight{
  background: rgb(150, 210, 151);
  padding: 0.2rem 1.4rem;
}
.error-alert{
  font-size: 0.7rem;
  margin-top: 0.5rem;
}
</style>