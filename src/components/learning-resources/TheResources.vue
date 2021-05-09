<template>
  <base-card class="change-tabs">
    <base-button
      @click="setSelectedTab('stored-resources')"
      type="button"
      :mode="StoredResourceButtonClass"
      >Stored Tasks</base-button
    >
    <base-button
      @click="setSelectedTab('add-resource')"
      type="button"
      :mode="AddResourceButtonClass"
      >Add Task</base-button
    >
  </base-card>
  <keep-alive>
    <component :is="selectedTab"></component>
  </keep-alive>
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
          title: 'Read Official Guide',
          description: 'The Official VueJS documentation!',
          link: 'https://www.vuejs.org'
        },
        {
          id: 'google',
          title: 'Google About Vue',
          description: 'Learn how to google stuff!',
          link: 'https://www.google.com'
        }
      ]
    };
  },
  computed: {
    StoredResourceButtonClass() {
      return this.selectedTab === 'stored-resources'
        ? 'change selected'
        : 'change';
    },
    AddResourceButtonClass() {
      return this.selectedTab === 'add-resource' ? 'change selected' : 'change';
    }
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
    addResource(title, description, url) {
      const newResource = {
        id: new Date().toISOString(),
        title: title,
        description: description,
        link: url
      };
      this.storedResources.unshift(newResource);
      this.selectedTab = 'stored-resources';
    }
  },
  provide() {
    return {
      resources: this.storedResources,
      addResource: this.addResource
    };
  }
};
</script>
<style scoped>
.change-tabs {
  display: flex;
  justify-content: space-around;
}
</style>
