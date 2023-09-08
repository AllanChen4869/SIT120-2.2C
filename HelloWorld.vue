<template>
  <div class="gamehub">
    <header>
      <nav>
        <div class="logo">GameHub</div>
        <ul>
          <li><a href="#">Home</a></li>
          <li><a href="#">Games</a></li>
          <li><a href="#">Forums</a></li>
          <li><a href="#">Profile</a></li>
          <li><a href="#" @click="addToCart">Cart ({{ cartItems.length }})</a></li>
        </ul>
      </nav>
    </header>
    
    <main>
      <section class="Hot">
        <h1>Welcome to GameHub</h1>
        <p>Discover the best games and connect with gamers worldwide.</p>
        <router-link to="/join" class="cta-button">Join Now</router-link>
      </section>
      
      <section class="featured-games">
        <div class="game-card">
          <img src="https://image.api.playstation.com/vulcan/ap/rnd/202211/0914/TvcIHkYqqln1RGbaFqBeuFp6.jpg" alt="Game 1">
          <h2>The Witcher 3: Wild Hunt</h2>
          <p>An open-world RPG game with fantasy.</p>
          <button class="buy-button" @click="buyGame(1)">Buy Now</button>
        </div>

        <div class="game-card">
          <img src="https://cdn.akamai.steamstatic.com/steam/apps/1086940/capsule_616x353.jpg?t=1692294127" alt="Game 2">
          <h2>Baldur's Gate 3</h2>
          <p>One of best strategy RPG game in the world.</p>
          <button class="buy-button" @click="buyGame(2)">Buy Now</button>
        </div>
      </section>
      
      <section class="user-profile">
        <h2>User Profile</h2>
        <img src="avatar.jpg" alt="User Avatar" class="avatar">
        <p>Welcome, {{ username }}</p>
        <button @click="customizeProfile">Customize Profile</button>
      </section>
      
      <section class="shopping-cart">
        <h2>Shopping Cart</h2>
        <ul>
          <li v-for="item in cartItems" :key="item.id">
            {{ item.title }} - ${{ item.price }}
          </li>
        </ul>
        <button @click="checkout">Checkout</button>
      </section>
    </main>
    
    <footer>
      <p>&copy; 2023 GameHub. All rights reserved.</p>
    </footer>
  </div>
</template>

<script>
export default {
  name: "GameHub",
  data() {
    return {
      cartItems: [],
      username: "User123", // You can fetch the username from the user's profile
    };
  },
  methods: {
    addToCart() {
      // Add items to the cart
      // You can fetch game data from an API and add it to cartItems
      this.cartItems.push({ id: 1, title: "Game Title 1", price: 19.99 });
    },
    buyGame(gameId) {
      // Implement game purchase logic
      // You can fetch game data from an API and complete the purchase
      console.log(`Purchased game with ID ${gameId}`);
    },
    customizeProfile() {
      // Redirect to the profile customization page or show a modal
      console.log("Customize Profile");
    },
    checkout() {
      // Implement the checkout process, including payment and download keys
      console.log("Checkout");
    },
  },
};
</script>

<style scoped>
/* Add your CSS styles here */
.gamehub {
  font-family: Arial, sans-serif;
  background-color: #121212;
  color: #fff;
}

header {
  background-color: #007acc;
  padding: 10px 0;
}

nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 1200px;
  margin: 0 auto;
}

.logo {
  font-size: 24px;
  font-weight: bold;
  color: #fff;
}

ul {
  list-style: none;
  display: flex;
}

ul li {
  margin-right: 20px;
}

a {
  text-decoration: none;
  color: #fff;
}

main {
  max-width: 1200px;
  margin: 20px auto;
  padding: 0 20px;
}

.Hot {
  background-color: #005580;
  color: #fff;
  text-align: center;
  padding: 40px 0;
  border-radius: 10px;
}

.cta-button {
  display: inline-block;
  background-color: #ff5722;
  color: #fff;
  padding: 10px 20px;
  text-decoration: none;
  border-radius: 5px;
  margin-top: 20px;
  transition: background-color 0.3s ease;
}

.cta-button:hover {
  background-color: #e64a19;
}

.featured-games {
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
  margin-top: 20px;
}

.game-card {
  background-color: #2a2a2a;
  color: #fff;
  border-radius: 10px;
  padding: 20px;
  width: 300px;
  margin: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
  transition: transform 0.3s ease;
}

.game-card:hover {
  transform: scale(1.05);
}

.game-card img {
  max-width: 100%;
  border-radius: 5px;
}

.game-card h2 {
  font-size: 18px;
  margin-top: 10px;
}

.game-card p {
  font-size: 14px;
  margin-top: 10px;
}

.buy-button {
  background-color: #ff5722;
  color: #fff;
  padding: 8px 16px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  margin-top: 10px;
  transition: background-color 0.3s ease;
}

.buy-button:hover {
  background-color: #e64a19;
}

.user-profile {
  background-color: #2a2a2a;
  color: #fff;
  border-radius: 10px;
  padding: 20px;
  margin-top: 20px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
  text-align: center;
}

.avatar {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  margin: 20px auto;
  display: block;
}

.shopping-cart {
  background-color: #2a2a2a;
  color: #fff;
  border-radius: 10px;
  padding: 20px;
  margin-top: 20px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
}

.shopping-cart ul {
  list-style: none;
  padding: 0;
}

.shopping-cart ul li {
  margin: 10px 0;
}

.checkout {
  background-color: #ff5722;
  color: #fff;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  margin-top: 10px;
  transition: background-color 0.3s ease;
}

.checkout:hover {
  background-color: #e64a19;
}

footer {
  background-color: #2a2a2a;
  color: #fff;
  text-align: center;
  padding: 10px 0;
}
</style>
