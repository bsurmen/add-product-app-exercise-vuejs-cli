<template>
  <div class="row product-container">
    <app-product v-for="(product, index) in productList" :key="index">
      <img
        class="card-img-top"
        :src="product.selectedImage == null ? imgPath : product.selectedImage"
        :alt="product.title"
      />
      <div class="card-body">
        <h5 class="card-title">{{ product.title }}</h5>
        <small> <strong>Item Number : </strong> {{ product.count }} </small>
        <br />
        <small> <strong>Price : </strong> {{ product.price }}</small>
        <br />
        <small> <strong>Total : </strong> {{ product.totalPrice }} </small>
      </div>
    </app-product>
  </div>
</template>

<script>
import Product from "./Product";
import { eventBus } from "../main";

export default {
  components: {
    appProduct: Product,
  },
  data() {
    return {
      productList: [],
      imgPath: require("../assets/default.png"),
    };
  },
  created() {
    eventBus.$on("productAdded", (product) => {
      if (this.productList.length < 10) {
        this.productList.push(product);
        eventBus.$emit("progressBarUpdated", this.productList.length);
      } else {
        alert("You cannot add more product!");
      }
    });
  },
};
</script>
