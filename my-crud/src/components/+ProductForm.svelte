<script>
    export let product = {};
    export let onSubmit;
  
    const handleSubmit = () => {
      onSubmit(product);
    };
  </script>
  
  <form on:submit|preventDefault={handleSubmit}>
    <label for="name">Nombre:</label>
    <input type="text" id="name" bind:value={product.name} />
  
    <label for="price">Precio:</label>
    <input type="number" id="price" step="0.01" bind:value={product.price} />
  
    <button type="submit">Guardar</button>
  </form>
  

