<template>
   <div className="card-container">
    <slot></slot>
   </div>
</template>

<style scoped>
.card-container {
  box-shadow: 1px 1px 5px 3px rgb(197, 197, 197);
  max-width: 50vw;
  padding: 0.4rem 0.5rem;
  margin: auto;
  margin-top: 0.2rem;
  border-radius: 0.3rem;
  overflow: hidden;
}
</style>