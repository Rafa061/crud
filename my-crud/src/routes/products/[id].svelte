<script>
    import { onMount } from 'svelte';
    import { navigate } from 'svelte-routing';
  
    let product = {};
  
    const fetchProduct = async () => {
      const productId = params.id;
  
      try {
        const response = await fetch(`http://localhost:3000/api.js/products/${productId}`);
        if (!response.ok) {
          throw new Error('Error al obtener el producto');
        }
  
        product = await response.json();
      } catch (error) {
        console.error(error.message);
      }
    };
  
    const updateProduct = async () => {
      const productId = params.id;
  
      try {
        const response = await fetch(`http://localhost:3000/api.js/products/${productId}`, {
          method: 'PUT',
          headers: {
            'Content-Type': 'application/json',
          },
          body: JSON.stringify(product),
        });
  
        if (!response.ok) {
          throw new Error('Error al actualizar el producto');
        }
        navigate('/products');
      } catch (error) {
        console.error(error.message);
      }
    };
  
    onMount(() => {
      fetchProduct();
    });
  </script>
  <svelte:head>
    <title>{`Editar Producto - ${product.name || ''}`}</title>
  </svelte:head>
  
  <div>
    <h2 class="text-2xl font-bold mb-4">{`Editar Producto - ${product.name || ''}`}</h2>
    {#if Object.keys(product).length === 0}
      <p>Cargando...</p>
    {:else}
      <form on:submit|preventDefault={updateProduct}>
        <label for="name">Nombre:</label>
        <input type="text" id="name" bind:value={product.name} />
        <label for="price">Precio:</label>
        <input type="number" id="price" step="0.01" bind:value={product.price} />
        <button type="submit">Guardar cambios</button>
      </form>
    {/if}
  </div>
  
  