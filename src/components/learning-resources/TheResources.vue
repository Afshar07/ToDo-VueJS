<template>
  <base-card>
    <base-button @click="setSelectedTab('stored-resources')"
      >Stored Resources</base-button
    >
    <base-button @click="setSelectedTab('add-resource')"
      >Add Resource</base-button
    >
  </base-card>

  <component :is="selectedTab"></component>
</template>

<script>
import StoredResources from './StoredResources.vue';
import AddResource from './AddResource.vue';
export default {
  components: {
    StoredResources,
    AddResource
  },
  data() {
    return {
      selectedTab: 'stored-resources',
      storedResources: [
        {
          id: 'official-guide',
          title: 'Official Guide',
          description: 'The Official VueJS documentation!',
          link: 'https://www.vuejs.org'
        },
        {
          id: 'google',
          title: 'Google',
          description: 'Learn how to google stuff!',
          link: 'https://www.google.com'
        }
      ]
    };
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    }
  },
  provide() {
    return {
      resources: this.storedResources
    };
  }
};
</script>
