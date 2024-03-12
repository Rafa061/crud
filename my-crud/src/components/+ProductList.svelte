<script>
  export let products = [];

  const deleteProduct = (productId) => {
  };
</script>

<ul>
  {#each products as product (product.id)}
    <li key={product.id}>
      {product.name} - ${product.price.toFixed(2)}
      <button on:click={() => deleteProduct(product.id)}>Eliminar</button>
      <a href={`/products/${product.id}`}>Editar</a>
    </li>
  {/each}
</ul>