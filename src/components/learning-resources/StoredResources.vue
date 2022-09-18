<template>
<!-- Could have also named StoredResources as TheResources since it is the only one in app, but StoredResources better explains what this componenent is -->
   <ul>
      <learning-resource 
      v-for="resource in resources" 
      :title="resource.title"
      :description="resource.description"
      :link="resource.link"
      :className="resource.class"
      :id="resource.id"
      :key="resource.id"
      >
     <!--  @onRemoveResource="$emit('onRemoveResource', $event)" -->
      <!-- the variable "$event" contains the data that is transferred with the event. -->
      </learning-resource>
    </ul>
</template>

<script>
import LearningResource from './LearningResource.vue';
export default{
  components: {
    LearningResource,
  },
  inject: ['resources'],
  // props: ['resources'],
 /*  emits:['onRemoveResource'] */
}
</script>

<style scoped>
li {
  margin-bottom: 0.5rem;
  list-style: none;
}

ul {
  margin-top: 0.5rem;
  padding: 0;
}
</style>
