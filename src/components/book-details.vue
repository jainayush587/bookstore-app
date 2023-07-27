<template>
    <div v-if="book" class="book-details">
      <img :src="book.coverImage" alt="Book Cover" class="book-cover" />
      <h2 class="book-title">{{ book.title }}</h2>
      <p class="book-author">{{ book.author }}</p>
      <p class="book-description">{{ book.description }}</p>
      <button @click="addToCart(book)">Add to Cart</button>
    </div>
    <div v-else>
      <p>No book selected</p>
    </div>
</template>

<script>
export default {
name: 'BookDetails',
props: {
    book: {
    type: Object,
    default: null,
    },
},
methods: {
    addToCart(book) {
    this.$emit('add-to-cart', book);
    },
},
};
</script>

<style scoped>
/* Add CSS styles for the book details here */
</style>
  