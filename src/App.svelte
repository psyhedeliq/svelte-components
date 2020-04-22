<script>
  import Product from "./Product.svelte";
  import Modal from "./Modal.svelte";

  let products = [
    {
      id: "p1",
      title: "A Book",
      price: 9.99
    }
  ];

  let showModal = false;
  let closeable = false;

  const addToCart = event => {
    console.log(event);
  };

  const deleteProduct = event => {
    console.log(event.detail);
  };

  const showModalOnScreen = () => {
    showModal = true;
  };

  const cancelModal = () => {
    showModal = false;
  };

  const closeModal = () => {
    showModal = false;
  };
</script>

<!-- title={product.title}
    price={product.price}
		another way to write the above props down to display them is:
		{...products} -->

{#each products as product}
  <Product {...product} on:add-to-cart={addToCart} on:delete={deleteProduct} />
{/each}

<button on:click={showModalOnScreen}>Show Modal</button>

{#if showModal}
  <Modal on:cancel={cancelModal} on:close={closeModal} let:didAgree={closeable}>
    <h1 slot="header">Hello my friend!</h1>
    <p>This works :D</p>
    <button slot="footer" on:click={closeModal} disabled={!closeable}>
      Confirm
    </button>
  </Modal>
{/if}
