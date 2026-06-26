<template>
  <div class="card">
    <img :src="property.image" :alt="property.title" />

    <div
      v-if="!property.available"
      class="badge"
    >
      Not Available
    </div>

    <h3>{{ property.title }}</h3>

    <p><strong>Location:</strong> {{ property.location }}</p>

    <p><strong>Type:</strong> {{ property.type }}</p>

    <p><strong>Price:</strong> R{{ property.price }}</p>

    <button @click="toggleBookmark">
      {{ bookmarked ? "★ Bookmarked" : "☆ Bookmark" }}
    </button>
  </div>
</template>

<script>
export default {
  props: {
    property: Object
  },

  data() {
    return {
      bookmarked: false
    }
  },

  methods: {
    toggleBookmark() {
      this.bookmarked = !this.bookmarked
    }
  }
}
</script>

<style scoped>
.card {
  border: 1px solid #ddd;
  border-radius: 10px;
  overflow: hidden;
  padding: 10px;
  position: relative;
  background: white;
}

img {
  width: 100%;
  height: 500px;
  object-fit: cover;
}

.badge {
  position: absolute;
  top: 10px;
  right: 10px;
  background: crimson;
  color: white;
  padding: 5px 10px;
  border-radius: 2px;
}

button {
  margin-top: 10px;
  padding: 9px;
  cursor: pointer;
  background-color: crimson;
  color: white;
  font-size: 1rem;
  text-align: center;
  border-radius: 5px;
}
</style>