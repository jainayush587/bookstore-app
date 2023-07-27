<template>
    <div class="cart">
      <button class="cart-toggle" @click="toggleCart">{{ cart.length }} items in Cart</button>
      <transition name="cart-slide">
        <div v-if="showCart" class="cart-drawer">
          <h2>Cart</h2>
          <div v-if="cart.length === 0">Your cart is empty</div>
          <div v-else>
            <div v-for="item in cart" :key="item.id" class="cart-item">
              <div class="item-info">
                <h3 class="item-title">{{ item.title }}</h3>
                <p class="item-author">{{ item.author }}</p>
              </div>
              <div class="item-actions">
                <button @click="removeFromCart(item)">Remove</button>
              </div>
            </div>
            <div class="cart-total">Total Items: {{ cart.length }}</div>
          </div>
        </div>
      </transition>
    </div>
  </template>
  
  <script>
  export default {
    name: 'BookCart',
    props: {
      cart: {
        type: Array,
        required: true,
      },
    },
    data() {
      return {
        showCart: false,
      };
    },
    methods: {
      toggleCart() {
        this.showCart = !this.showCart;
      },
      removeFromCart(item) {
        this.$emit('remove-from-cart', item);
      },
    },
  };
  </script>
  
  <style>
  /* CSS for the Cart Component */
  .cart {
    position: relative;
  }
  
  .cart-toggle {
    position: fixed;
    bottom: 20px;
    right: 20px;
    padding: 10px;
    background-color: #007bff;
    color: #fff;
    border: none;
    cursor: pointer;
    border-radius: 5px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    z-index: 2;
  }
  
  .cart-drawer {
    position: fixed;
    top: 0;
    right: 0;
    width: 300px;
    height: 100%;
    background-color: #f9f9f9;
    box-shadow: -2px 0 4px rgba(0, 0, 0, 0.1);
    padding: 20px;
    transform: translateX(100%);
    transition: transform 0.3s ease-in-out;
    z-index: 1;
  }
  
  /* .cart-slide-enter-active,
  .cart-slide-leave-active {
    transition: transform 0.3s ease-in-out;
  } */
  
  /* .cart-slide-enter,
  .cart-slide-leave-to {
    transform: translateX(0);
  } */
  
  .cart-item {
    display: flex;
    align-items: center;
    margin-bottom: 10px;
    border-bottom: 1px solid #ddd;
    padding-bottom: 10px;
  }
  
  .cart-total {
    margin-top: 20px;
  }
  
  /* Add other styles as needed */
  </style>
  