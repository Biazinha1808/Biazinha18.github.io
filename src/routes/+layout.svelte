<script>
  import { onMount } from 'svelte';
  import { items } from '$lib/items.js';

  let cart = [];

  function addToCart(item) {
    cart = [...cart, item];
  }

  function removeFromCart(index) {
    cart = cart.filter((_, i) => i !== index);
  }
</script>

<!-- ✅ Navbar corrigida -->
<nav class="navbar">
  <div class="container">
    <a class="navbar-brand" href="https://www.lojasrenner.com.br/c/feminino/-/N-4zo6za?s_icid=230228_MENU_FEM_VERTUDO">Home</a>
  </div>
</nav>

<main>
  <h1>🛍️ Loja de Moda Feminina</h1>
  
  <div class="products">
    {#each items as item}
      <div class="product">
        <img src={item.image} alt={item.name} />
        <h2>{item.name}</h2>
        <p class="price">{item.price}</p>
        <button on:click={() => addToCart(item)}>Adicionar ao Carrinho</button>
      </div>
    {/each}
  </div>

  <h2>🛒 Carrinho</h2>
  <ul class="cart">
    {#each cart as item, index}
      <li>
        <img src={item.image} alt={item.name} class="cart-img"/>
        <span>{item.name} - {item.price}</span>
        <button on:click={() => removeFromCart(index)} class="remove-btn">❌</button>
      </li>
    {/each}
  </ul>
</main>

<!-- ✅ CSS corrigido -->
<style>
  .navbar {
    background: #ff69b4;
    padding: 15px;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .container {
    display: flex;
    gap: 20px;
  }

  .navbar-brand {
    color: white;
    font-size: 18px;
    text-decoration: none;
    font-weight: bold;
  }

  .navbar-brand:hover {
    text-decoration: underline;
  }

  main {
    font-family: 'Arial', sans-serif;
    padding: 20px;
    max-width: 1200px;
    margin: auto;
  }

  .products {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 20px;
    padding: 20px;
  }

  .product {
    border: 1px solid #ddd;
    padding: 15px;
    border-radius: 10px;
    text-align: center;
    background: #fff;
    box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.1);
  }

  .product img {
    width: 100%;
    height: 180px;
    object-fit: cover;
    border-radius: 5px;
  }

  .cart {
    list-style: none;
    padding: 0;
    max-width: 600px;
    margin: auto;
  }

  .cart li {
    display: flex;
    align-items: center;
    justify-content: space-between;
    background: #fff;
    padding: 10px;
    margin: 10px 0;
    border-radius: 5px;
    box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.1);
  }

  .cart-img {
    width: 50px;
    height: 50px;
    object-fit: cover;
    border-radius: 5px;
  }

  .remove-btn {
    background: #ff4d4d;
    font-size: 14px;
    padding: 5px;
  }

  .remove-btn:hover {
    background: #cc0000;
  }
</style>
