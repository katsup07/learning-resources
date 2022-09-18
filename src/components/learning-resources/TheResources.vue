<template>
  <div>
    <base-card>
      <base-button @click="setSelectedTab('stored-resources')" :mode="storedResButtonMode">Stored Resources</base-button >
      <base-button @click="setSelectedTab('add-resource')" :mode="addResButtonMode">Add Resource</base-button>
    </base-card>

    <!-- Tells which component to render, either stored-resources or add-resource -->
    <keep-alive>
      <component
      :is="selectedTab"
      ></component>
    </keep-alive>
     <!--  :resources="storedResources" -->
     <!--  @onRemoveResource="removeResource" -->
  <!--     @onAddResource="addResource" -->

    <!-- <component :is=...> can do the same as below  -->
    <!-- <stored-resources 
    @onRemoveResource="removeResource" 
    :resources="storedResources" 
    v-if="selectedTab === 'stored-resources'">
    </stored-resources>

    <keep-alive>
      <add-resource 
      @onAddResource="addResource" 
      v-if="selectedTab === 'add-resource'"></add-resource>
    </keep-alive> -->

  </div>
</template>
<script>
import StoredResources from './StoredResources.vue';
import AddResource from './AddResource.vue';

export default {
  components: {
    AddResource,
    StoredResources,
  },
  provide(){
    return {
      resources: this.storedResources,
      addResource: this.addResource,
      removeResource: this.removeResource,
    }
  },
  data(){
    return {
      selectedTab: 'stored-resources',
      storedResources:[
        {
          id: 'official-guide', 
          title: 'Vue Official Guide', 
          description: 'The official Vue.js documentation',
          link: 'https://vuejs.org',
          class: 'green',
          },
        {
          id: 'google', 
          title: 'Google', 
          description: 'Learn to google',
          link: 'https://google.com',
          class: 'pink',
          },
        {
          id: 'C++', 
          title: 'C++', 
          description: 'Learn C++',
          link: 'https://cplusplus.com/',
          class: 'purple',
          },
      ],
    }
  },
  computed: {
    storedResButtonMode(){
      return this.selectedTab === 'add-resource' ? null : 'highlight';
    },
    addResButtonMode(){
      return this.selectedTab ==='stored-resources' ? null : 'highlight';
    }
  },
  methods: {
    setSelectedTab(tab){
      this.selectedTab = tab;
      this.$emit('onSetCurrentDisplay', {id: tab});
      console.log('toggling selection', this.selectedTab);
    },
     removeResource(resourceId){
      console.log('TheResources removeResource()...', resourceId);
      /* see note below for why filter() won't work here */
      const index = this.storedResources.findIndex(res => res.id === resourceId);
      this.storedResources.splice(index, 1);
    },
    addResource(newResource){
      console.log('adding resource...', newResource);
      this.storedResources.unshift(newResource);
      this.selectedTab = 'stored-resources';
    },
  }
}

// ! This won't work, since we override the old array that stored all the resource data, so other components will still have old array and won't be notified of any changes. Hence, the view on screen will not change, eventhough the state data does.
/*  removeResource(resourceId){
      this.storedResources = this.storedResources.filter( res =>  res.id !== resourceId);
*/
</script>

