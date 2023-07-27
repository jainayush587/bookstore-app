<template>
  <div class="app">
    <div class="header">
      <h1 class="title">Bookstore</h1>
    </div>
    <div class="container">
      <book-list :books="books" @add-to-cart="addToCart" />
      <!-- <book-details :book="selectedBook" @add-to-cart="addToCart" /> -->
      <book-cart :cart="cart" @remove-from-cart="removeFromCart" />
    </div>
  </div>
</template>

<script>
import BookList from './components/books-list.vue';
//import BookDetails from './components/book-details.vue';
import BookCart from './components/cart.vue';

export default {
  name: 'App',
  data() {
    return {
      books: [
        {
          id: 1,
          title: 'Book 1',
          author: 'Author 1',
          description: 'Description of Book 1',
          coverImage: 'book.jpg',
        },
        {
          id: 2,
          title: 'Book 2',
          author: 'Author 2',
          description: 'Description of Book 2',
          coverImage: 'book.jpg',
        },
        {
          id: 3,
          title: 'Book 3',
          author: 'Author 3',
          description: 'Description of Book 3',
          coverImage: 'book.jpg',
        },
        {
          id: 4,
          title: 'Book 4',
          author: 'Author 4',
          description: 'Description of Book 4',
          coverImage: 'book.jpg',
        },
        {
          id: 5,
          title: 'Book 5',
          author: 'Author 5',
          description: 'Description of Book 5',
          coverImage: 'book.jpg',
        },
        {
          id: 6,
          title: 'Book 6',
          author: 'Author 6',
          description: 'Description of Book 6',
          coverImage: 'book.jpg',
        },
        // Add more books as needed
      ],
      selectedBook: null,
      cart: [],
    };
  },
  methods: {
    addToCart(book) {
      if (!this.cart.find((item) => item.id === book.id)) {
        this.cart.push(book);
      }
    },
    removeFromCart(item) {
      const index = this.cart.findIndex((book) => book.id === item.id);
      if (index !== -1) {
        this.cart.splice(index, 1);
      }
    },
  },
  components: {
    BookList,
    //BookDetails,
    BookCart,
  },
};
</script>

<style lang="less">
html {
  font-family: sans-serif;
}
.app{
  width: 95%;
  margin: auto;

  .header{
    border-bottom: 1px solid #e6e6e6;
    padding: 0 10px;
  }

  .container{
    margin-top: 10px;
  }
}
/* Add CSS styles for the app and header here */
</style>
