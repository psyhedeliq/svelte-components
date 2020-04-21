<script>
  import Product from "./Product.svelte";

  const addToCart = event => {
    console.log(event);
  };

  const deleteProduct = event => {
    console.log(event.detail);
  };
</script>

<Product
  productTitle="A Book"
  on:add-to-cart={addToCart}
  on:delete={deleteProduct} />
