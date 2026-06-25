<template>
  <div>
    <Header :count="filteredProperties.length" />

    <div class="controls">
      <SearchBar v-model="searchQuery" />
      <SortDropdown v-model="sortOrder" />
    </div>

    <div class="grid">
      <PropertyCard
        v-for="property in filteredProperties"
        :key="property.id"
        :property="property"
      />
    </div>
  </div>
</template>

<script>
import Header from "./components/Header.vue"
import SearchBar from "./components/SearchBar.vue"
import SortDropdown from "./components/SortDropdown.vue"
import PropertyCard from "./components/PropertyCard.vue"
import properties from "./properties"

export default {
  components: {
    Header,
    SearchBar,
    SortDropdown,
    PropertyCard
  },

  data() {
    return {
      searchQuery: "",
      sortOrder: "",
      properties
    }
  },

  computed: {
    filteredProperties() {
      let result = this.properties.filter(property =>
        property.title
          .toLowerCase()
          .includes(this.searchQuery.toLowerCase()) ||
        property.location
          .toLowerCase()
          .includes(this.searchQuery.toLowerCase())
      )

      if (this.sortOrder === "asc") {
        result.sort((a, b) => a.price - b.price)
      }

      if (this.sortOrder === "desc") {
        result.sort((a, b) => b.price - a.price)
      }

      return result
    }
  }
}
</script>

<style>
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: #f5f5f5;
}

.controls {
  display: flex;
  justify-content: center;
  gap: 15px;
  margin: 20px;
}

.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(500px, 1fr));
  gap: 20px;
  padding: 20px;
}
</style>