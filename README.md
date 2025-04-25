<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Blox Fruits Account Shop</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@500&display=swap');

    body {
      font-family: 'Orbitron', sans-serif;
      margin: 0;
      padding: 0;
      background-color: #0f0f0f;
      color: #fff;
    }
    header {
      background-color: #111;
      padding: 20px;
      text-align: center;
      border-bottom: 2px solid #00ffcc;
    }
    h1 {
      font-size: 2.5rem;
      color: #00ffcc;
      text-shadow: 0 0 10px #00ffcc;
    }
    .search-bar {
      padding: 20px;
      text-align: center;
    }
    .search-bar input {
      padding: 10px;
      width: 300px;
      border-radius: 6px;
      border: none;
      font-size: 1rem;
    }
    .container {
      display: flex;
      flex-direction: column;
      gap: 20px;
      padding: 30px;
    }
    .card {
      background: #1a1a1a;
      padding: 20px;
      border-radius: 12px;
      box-shadow: 0 0 15px rgba(0, 255, 204, 0.3);
      transition: transform 0.2s, box-shadow 0.2s;
      width: 100%;
    }
    .card:hover {
      transform: translateY(-5px);
      box-shadow: 0 0 20px rgba(0, 255, 204, 0.6);
    }
    .card h2 {
      font-size: 1.2em;
      margin-bottom: 10px;
      color: #00ffcc;
    }
    .card p {
      margin: 5px 0;
    }
    .price {
      color: #00ff66;
      font-weight: bold;
    }
    .delivery-time {
      color: #ccc;
      font-size: 0.9em;
    }
    .add-to-cart, .description-btn {
      margin-top: 10px;
      display: inline-block;
      background: #00ffcc;
      color: #0f0f0f;
      padding: 10px 15px;
      border: none;
      border-radius: 6px;
      cursor: pointer;
      text-align: center;
      font-weight: bold;
      transition: background 0.3s;
      margin-right: 5px;
    }
    .add-to-cart:hover, .description-btn:hover {
      background: #00e6b8;
    }
    .checkout {
      background: #111;
      padding: 30px 20px;
      text-align: center;
      border-top: 2px solid #00ffcc;
    }
    .checkout h2 {
      font-size: 2rem;
      color: #00ffcc;
    }
    .checkout ul {
      list-style: none;
      padding: 0;
      margin: 10px 0;
    }
    .checkout ul li {
      color: #ccc;
      margin-bottom: 10px;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
    .remove-btn {
      background: red;
      color: #fff;
      border: none;
      padding: 5px 10px;
      border-radius: 6px;
      cursor: pointer;
      font-weight: bold;
    }
    .checkout-btn {
      background: #00ffcc;
      color: #0f0f0f;
      padding: 10px 20px;
      border: none;
      border-radius: 6px;
      cursor: pointer;
      font-weight: bold;
      transition: background 0.3s;
    }
    .checkout-btn:hover {
      background: #00e6b8;
    }
    footer {
      background-color: #111;
      padding: 40px 20px;
      text-align: center;
      border-top: 2px solid #00ffcc;
      margin-top: 40px;
    }
    .about-section {
      max-width: 800px;
      margin: auto;
    }
    .about-section h2 {
      color: #00ffcc;
      font-size: 2rem;
      margin-bottom: 10px;
    }
    .about-section p {
      color: #ccc;
      line-height: 1.6;
    }
    .team {
      margin-top: 20px;
    }
    .team h3 {
      color: #00ffcc;
      margin-bottom: 10px;
    }
    .team-member {
      color: #aaa;
    }
    .description-content {
      margin-top: 10px;
      background: #222;
      padding: 10px;
      border-radius: 8px;
      display: none;
    }
    .description-content img {
      max-width: 100px;
      margin: 5px;
      border-radius: 6px;
      cursor: pointer;
    }
    #image-modal {
      display: none;
      position: fixed;
      z-index: 9999;
      left: 0;
      top: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.8);
      justify-content: center;
      align-items: center;
    }
    #image-modal img {
      max-width: 90%;
      max-height: 90%;
    }
    .close {
      position: absolute;
      top: 20px;
      right: 40px;
      font-size: 40px;
      color: white;
      cursor: pointer;
    }
    .whatsapp-button {
      position: fixed;
      bottom: 20px;
      right: 20px;
      z-index: 1000;
      background-color: #25D366;
      color: white;
      border: none;
      border-radius: 50%;
      width: 60px;
      height: 60px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 28px;
      box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
      text-decoration: none;
    }
  </style>
</head>
<body>
  <header>
    <h1>Blox Fruits Account Shop</h1>
  </header>
  <div class="search-bar">
    <input type="text" placeholder="Search accounts..." id="search-input">
  </div>
  <div class="container"></div>

  <div class="checkout">
    <h2>Your Cart</h2>
    <ul id="cart-list"></ul>
    <p id="total-price">Total: $0</p>
    <button class="checkout-btn" onclick="proceedToCheckout()">Proceed to Checkout</button>
  </div>

  <div id="image-modal">
    <span class="close">&times;</span>
    <img id="modal-img">
  </div>

  <a href="https://wa.me/7982413700" class="whatsapp-button" target="_blank" title="Chat on WhatsApp">
    <img src="https://i.postimg.cc/Yq8QP6LZ/sm-5b321c99945a2.jpg" alt="WhatsApp" width="60" height="60" style="border-radius: 50%; object-fit: cover;">
    <i class="fab fa-whatsapp"></i>
  </a>

  <footer>
    <div class="about-section">
      <h2>About Us</h2>
      <p>Welcome to Blox Fruits Account Shop! We're passionate gamers bringing you top-tier Roblox Blox Fruits accounts. Our goal is to make your experience legendary by providing powerful accounts at fair prices.</p>
      <div class="team">
        <h3>Meet the Team</h3>
        <p class="team-member">👑 DevMasterX - Founder & Backend Wizard</p>
        <p class="team-member">🎨 PixelNinja - UI/UX Designer</p>
        <p class="team-member">⚙️ CodeGhost - Frontend Developer</p>
        <p class="team-member">🛡️ GameGuru - Game Analyst & Support</p>
      </div>
    </div>
  </footer>

  <script>
    const accounts = [
      { id: '001', details: 'Level 2569 | Permanent Fruit Combo | $100000 Beli', price: 20, images: ['https://via.placeholder.com/900x900?text=Account+001+Image+1', 'https://via.placeholder.com/1000x1000?text=Account+001+Image+2'] },
      { id: '002', details: 'Level 2551 | Permanent Fruit Combo | $100500 Beli', price: 21, images: ['https://via.placeholder.com/900x900?text=Account+002+Image+1', 'https://via.placeholder.com/1000x1000?text=Account+002+Image+2'] },
      { id: '003', details: 'Level 2552 | Permanent Fruit Combo | $101000 Beli', price: 22, images: ['https://via.placeholder.com/900x900?text=Account+003+Image+1', 'https://via.placeholder.com/1000x1000?text=Account+003+Image+2'] },
      { id: '004', details: 'Level 2553 | Permanent Fruit Combo | $101500 Beli', price: 23, images: ['https://via.placeholder.com/900x900?text=Account+004+Image+1', 'https://via.placeholder.com/1000x1000?text=Account+004+Image+2'] },
      { id: '005', details: 'Level 2554 | Permanent Fruit Combo | $102000 Beli', price: 24, images: ['https://via.placeholder.com/900x900?text=Account+005+Image+1', 'https://via.placeholder.com/1000x1000?text=Account+005+Image+2'] },
      { id: '006', details: 'Level 2555 | Permanent Fruit Combo | $102500 Beli', price: 25, images: ['https://via.placeholder.com/900x900?text=Account+006+Image+1', 'https://via.placeholder.com/1000x1000?text=Account+006+Image+2'] },
      { id: '007', details: 'Level 2556 | Permanent Fruit Combo | $103000 Beli', price: 26, images: ['https://via.placeholder.com/900x900?text=Account+007+Image+1', 'https://via.placeholder.com/1000x1000?text=Account+007+Image+2'] },
      { id: '008', details: 'Level 2557 | Permanent Fruit Combo | $103500 Beli', price: 27, images: ['https://via.placeholder.com/900x900?text=Account+008+Image+1', 'https://via.placeholder.com/1000x1000?text=Account+008+Image+2'] },
      { id: '009', details: 'Level 2558 | Permanent Fruit Combo | $104000 Beli', price: 28, images: ['https://via.placeholder.com/900x900?text=Account+009+Image+1', 'https://via.placeholder.com/1000x1000?text=Account+009+Image+2'] },
      { id: '010', details: 'Level 2559 | Permanent Fruit Combo | $104500 Beli', price: 29, images: ['https://via.placeholder.com/900x900?text=Account+010+Image+1', 'https://via.placeholder.com/1000x1000?text=Account+010+Image+2'] }
    ];

    const container = document.querySelector(".container");
    const modal = document.getElementById("image-modal");
    const modalImg = document.getElementById("modal-img");
    const closeBtn = document.querySelector(".close");
    const cartList = document.getElementById("cart-list");
    const totalPriceEl = document.getElementById("total-price");
    let cart = [];

    function renderAccounts(filtered = accounts) {
      container.innerHTML = "";
      filtered.forEach(account => {
        const card = document.createElement("div");
        card.className = "card";

        const descId = `desc-${account.id}`;

        let imagesHTML = account.images.map(img => `<img src="${img}" alt="${account.id}" onclick="showModal('${img}')">`).join('');

        card.innerHTML = `
          <h2>ID: ${account.id}</h2>
          <p>${account.details}</p>
          <p class="price">$${account.price}</p>
          <p class="delivery-time">Instant Delivery</p>
          <button class="add-to-cart" onclick="addToCart('${account.id}')">Add to Cart</button>
          <button class="description-btn" onclick="toggleDescription('${descId}')">Show Description</button>
          <div id="${descId}" class="description-content">
            ${imagesHTML}
            <p>Write now images are not available</p>
          </div>
        `;

        container.appendChild(card);
      });
    }

    renderAccounts();

    function showModal(src) {
      modal.style.display = "flex";
      modalImg.src = src;
    }

    function toggleDescription(id) {
      const content = document.getElementById(id);
      content.style.display = content.style.display === 'block' ? 'none' : 'block';
    }

    closeBtn.onclick = () => {
      modal.style.display = "none";
    };

    window.onclick = function(event) {
      if (event.target == modal) {
        modal.style.display = "none";
      }
    };

    document.getElementById("search-input").addEventListener("input", function() {
      const query = this.value.trim().toLowerCase();
      const filtered = accounts.filter(acc => acc.id.toLowerCase().includes(query));
      renderAccounts(filtered);
    });

    function addToCart(id) {
      const account = accounts.find(a => a.id === id);
      cart.push(account);
      updateCart();
    }

    function removeFromCart(index) {
      cart.splice(index, 1);
      updateCart();
    }

    function updateCart() {
      cartList.innerHTML = "";
      let total = 0;
      cart.forEach((item, index) => {
        const li = document.createElement("li");
        li.innerHTML = `${item.id} - $${item.price} <button class='remove-btn' onclick='removeFromCart(${index})'>Remove</button>`;
        cartList.appendChild(li);
        total += item.price;
      });
      totalPriceEl.textContent = `Total: $${total}`;
    }

    function proceedToCheckout() {
      alert(`Total amount due: $${cart.reduce((sum, item) => sum + item.price, 0)}`);
    }
  </script>
</body>
</html>

