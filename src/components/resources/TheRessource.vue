<template>
  <base-card>
    <base-button
      :mode="storeResButtonMode"
      @click="setSelectedTab('stored-ressource')"
    >
      Stored ressources
    </base-button>

    <base-button
      :mode="addResButtonMode"
      @click="setSelectedTab('add-ressource')"
    >
      add ressource
    </base-button>
  </base-card>
  <KeepAlive>
    <component :is="selectedTab"></component>
  </KeepAlive>
</template>

<script>
import StoredRessource from './StoredRessource.vue';
import AddRessource from './AddRessource.vue';
export default {
  components: {
    StoredRessource,
    AddRessource,
  },
  data() {
    return {
      selectedTab: 'stored-ressource',
    
      storedResources: [
        {
          id: 'official-guide',
          title: 'Official guide',
          description: 'this is the description ',
          link: 'https.vuejs.org',
        },
        {
          id: 'google',
          title: 'google',
          description: 'this is the description of google',
          link: 'https.google.com',
        },
      ],
    };
  },
  computed: {
    storeResButtonMode() {
      return this.selectedTab === 'stored-ressource' ? null : 'flat';
    },
    addResButtonMode() {
      return this.selectedTab === 'add-ressource' ? null : 'flat';
    },
  },
  provide() {
    return {
      storedResources: this.storedResources,
      AddRessource: this.AddRessource,
    };
  },

  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },

    AddRessource(title, description, url) {
      const newResource = {
        id: Date.now(),
        title: title,
        description: description,
        link: url,
      };

      this.storedResources.unshift(newResource);
      this.selectedTab = 'stored-ressource';
    },
  },
};
</script>
