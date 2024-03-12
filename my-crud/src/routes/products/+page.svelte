<svelte:head>
  <title>Mi Aplicación - Productos</title>
</svelte:head>
<script>
  
  let products = [
    { id: 1, name: 'Producto 1', price: 10.99, quantity: 5 },
    { id: 2, name: 'Producto 2', price: 24.99, quantity: 8 },
    ];
  let newProduct = { name: '', price: 0, quantity: 0 };
  const createProduct = () => { 
    products = [...products, { id: products.length + 1, ...newProduct }];
    newProduct = { name: '', price: 0, quantity: 0 };
  };
  const deleteProduct = (productId) => {
    products = products.filter((product) => product.id !== productId);
  };
</script>
<div>
  <header class="bg-gray-800 text-white p-4">
    <h1 class="text-2xl font-bold">Mi Aplicación</h1>
    <nav class="mt-2">
      <a href="/">Inicio</a>
      <a href="/products">Productos</a>
    </nav>
  </header>
  <main class="p-4">
    <h2 class="text-2xl font-bold mb-4">Productos</h2>
    <form on:submit|preventDefault={createProduct} class="mb-8">
      <div class="grid grid-cols-3 gap-4">
        <div>
          <label for="newProductName">Nombre:</label>
          <input type="text" id="newProductName" bind:value={newProduct.name} class="w-full p-2 border rounded" />
        </div>
        <div>
          <label for="newProductPrice">Precio:</label>
          <input type="number" id="newProductPrice" step="0.01" bind:value={newProduct.price} class="w-full p-2 border rounded" />
        </div>
        <div>
          <label for="newProductQuantity">Cantidad:</label>
          <input type="number" id="newProductQuantity" bind:value={newProduct.quantity} class="w-full p-2 border rounded" />
        </div>
      </div>
      <button type="submit" class="mt-4 bg-blue-500 text-white p-2 rounded">Crear Producto</button>
    </form>
    <ul>
        {#each products as product (product.id)}
          <li key={product.id} class="mb-6 p-4 border rounded">
            <div class="flex justify-between">
              <div>
                <h3 class="text-xl font-bold">{product.name}</h3>
                <p class="text-gray-600">Precio: ${product.price.toFixed(2)}</p>
                <p class="text-gray-600">Cantidad: {product.quantity}</p>
              </div>
              <div>
                <button on:click={() => deleteProduct(product.id)} class="bg-red-500 text-white p-2 rounded">Eliminar</button>
              </div>
            </div>
          </li>
        {/each}
      </ul>
  </main>
  <footer class="p-4 bg-gray-800 text-white text-center">
    isaac te falle 
    lo intente pero no pude hacer esta ver :=c
    pero lo intente y la luz no me ayudo tampoco
    
  </footer>
</div>

