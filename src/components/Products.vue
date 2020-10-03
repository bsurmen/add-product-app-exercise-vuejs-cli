<template>
  <div class="row product-container">
    <app-product v-for="(product, index) in productList" :key="index">
      <img
        class="card-img-top"
        src="../assets/default.png"
        alt="Card image cap"
      />
      <div class="card-body">
        <h5 class="card-title">Card title</h5>
        <small> <strong>Item Number : </strong> 1 </small>
        <br />
        <small> <strong>Price : </strong> 10 </small>
        <br />
        <small> <strong>Total : </strong> 10 </small>
      </div>
    </app-product>
  </div>
</template>

<script>
import Product from "./Product";

export default {
  components: {
    appProduct: Product,
  },
  data() {
    return {
      productList: [],
    };
  },
};
</script>
