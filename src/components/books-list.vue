<template>
    <div class="book-list">
      <div v-for="book in books" :key="book.id" class="book-card">
        <img :src="getImgUrl(book.coverImage)" alt="Book Cover" class="book-cover" />
        <h3 class="book-title">{{ book.title }}</h3>
        <p class="book-author">{{ book.author }}</p>
        <button class="cart-btn" @click="addToCart(book)">Add to Cart</button>
      </div>
    </div>
</template>

<script>
export default {
  name: 'BookList',
  props: {
    books: {
      type: Array,
      required: true,
    },
  },
  mounted(){
    console.log(this.books[0].coverImage);
  },
  methods: {
    addToCart(book) {
      this.$emit('add-to-cart', book);
    },
    getImgUrl(pic) {
      return require('../assets/'+pic)
    }
  },
};
</script>

<style lang="less" scoped>
.book-list {
  border: 1px solid #e6e6e6;
  padding: 10px;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;

  .book-card {
    background: #fff;
    border-radius: 5px;
    padding: 20px;
    text-align: center;
  }

  .book-card:hover{
    box-shadow: 0 3px 10px rgb(0 0 0 / 0.2);
  }
  .book-cover {
    max-width: 100%;
    height: auto;
  }
  .cart-btn{
    width: 100%;
    height: 40px;
    font-size: 16px;
    background: #52e000;
    font-weight: 600;
    color: #fff;
    border: none;
    border-radius: 2px;
    cursor: pointer;
  }
}




/* Add CSS styles for the book list and book card here */
</style>
  