<template>
  <li>
      <base-card>
            <div>
              <header>
                <h2 :className="className">{{title}}</h2>
              </header>
            </div>
            <p className="description">{{description}}</p>
            <div class="bottom">
              <nav><a :href="link">more...</a></nav>
              <base-button @click="removeResource(id)" mode="danger">delete</base-button>
            </div>
        </base-card>
    </li>
</template>

<script>
export default {
  props: ['className', 'title', 'description', 'link', 'id'],
  inject: ['removeResource'],
  // emits: ['onRemoveResource'],
  data(){
    return{

    }
  },
  methods: {
   /*  onRemoveResource(id){
      console.log("onRemoveResource", id);
      this.$emit('onRemoveResource', {id: id});
    } */
  }
}
</script>
<style scoped>
header {
  /* display: flex;
  justify-content: space-between;
  align-items: center; */
}

.bottom{
  display: flex;
  justify-content: space-between;
  align-items: center;
}
h2 {
  padding-bottom: 0.6rem;
  margin: 0;
}

li {
  margin: none;
}

a {
  color: orange;
  transition: color 0.35s;
}
a:hover {
  color: rgb(0, 55, 255);
}

.resources {
    box-shadow: 1px 1px 5px 3px rgb(197, 197, 197);
    max-width: 50vw;
    padding: 0.7rem;
    margin: auto;
    border-radius: 0.3rem;
}
  
.description, a {
    font-size: 0.8rem;
    margin-bottom: 0;
    margin-top: 0.4rem;
}

.pink{
  color: rgb(255, 134, 134);
}

  .orange{
     color: rgb(255, 172, 146);
  }
  .yellow{
     color: rgb(235, 255, 135);
  }
.green{
  color: rgb(146, 255, 170);
}
.blue{
   color: rgb(146, 182, 255);
}
.purple{
   color: rgb(157, 146, 255);
}
</style>