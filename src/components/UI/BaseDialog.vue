<template>
      <teleport to="body">
        <div class="container">
          <div @click="$emit('close')" class="modal-background"></div>
          <dialog open>
            <header>
              <slot name="header">
                <h2>{{title}}</h2> <!-- Default -->
              </slot>
            </header>
            <section>
              <slot name="default"></slot>
            </section>
            <menu><!-- default html element -->
              <slot name="actions">
                <base-button @click="$emit('close')">close</base-button>
              </slot>
            </menu>
          </dialog>
        </div>
      </teleport>
</template>

<script>
export default{
  props: {
    title: {
      type: String,
      required: false,
    }
  },
  emits: ['close'],
}
</script>
<style scoped>
  .modal-background {
    position: fixed;
    top: 0;
    left: 0;
    height: 100vh;
    width: 100%;
    background: rgba(0, 0, 0, 0.836);
    z-index: 10;
  }
dialog {
  position: fixed;
  top: 40vh;
  left: 35vh;
  width: 60%;
  z-index: 100;
  border-radius: 12px; 
  border: none;
  background: rgb(255, 255, 163);
  box-shadow: 0 2px 8px rgba(0,0,0,0.26);
  padding: 0;
  margin: 0;
  overflow: hidden;
}

header {
  background-color: rgb(56, 56, 56);
  color: rgb(246, 234, 0);
  width: 100%;
  padding: 0.5rem;
  overflow: hidden;
}

header h2 {
  margin: 0;
}

section {
  padding: 1rem;

}
menu {
  padding: 1rem;
  display: flex;
  justify-content: flex-end;
  margin: 0;
}


@media (min-width: 1768px){
  dialog {
    width: 40rem;
    left: calc(50%-20rem);
  }
}

@media (min-width: 168px){
  .dialog {
    width: 20rem;
    left: 50rem;
  }
}
</style>