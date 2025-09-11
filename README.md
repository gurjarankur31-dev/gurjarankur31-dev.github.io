<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Nifty & Bank Nifty Live Prices</title>
  <style>
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background-color: #1e1e2f;
      color: #ffffff;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
    }
    .container {
      background-color: #2b2b3d;
      padding: 30px 40px;
      border-radius: 15px;
      box-shadow: 0 4px 20px rgba(0,0,0,0.5);
      text-align: center;
    }
    h1 {
      margin-bottom: 20px;
      font-size: 2rem;
      color: #00d1b2;
    }
    .price-box {
      background-color: #3a3a5e;
      margin: 15px 0;
      padding: 20px;
      border-radius: 10px;
      transition: background-color 0.3s ease;
    }
    .price-box:hover {
      background-color: #4a4a7e;
    }
    .label {
      font-size: 1.2rem;
      margin-bottom: 8px;
      color: #ccc;
    }
    .price {
      font-size: 1.8rem;
      font-weight: bold;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Nifty & Bank Nifty Live Prices</h1>
    <div class="price-box">
      <div class="label">Nifty</div>
      <div id="nifty-price" class="price">Loading...</div>
    </div>
    <div class="price-box">
      <div class="label">Bank Nifty</div>
      <div id="banknifty-price" class="price">Loading...</div>
    </div>
  </div>

  <script>
    const apiKey = '7d5a824ec06d46e6888480cac97a6f95';
    const niftySymbol = '^NSEI';
    const bankNiftySymbol = '^NSEBANK';

    async function fetchPrice(symbol) {
      const url = `https://api.twelvedata.com/price?symbol=${symbol}&apikey=${apiKey}`;
      try {
        const response = await fetch(url);
        const data = await response.json();
        if(data.price) {
          return parseFloat(data.price).toFixed(2);
        } else {
          console.error("Error fetching price:", data);
          return "N/A";
        }
      } catch (error) {
        console.error("Fetch error:", error);
        return "Error";
      }
    }

    async function updatePrices() {
      const niftyPrice = await fetchPrice(niftySymbol);
      const bankNiftyPrice = await fetchPrice(bankNiftySymbol);

      document.getElementById('nifty-price').textContent = niftyPrice;
      document.getElementById('banknifty-price').textContent = bankNiftyPrice;
    }

    // Initial load
    updatePrices();

    // Update every 5 seconds
    setInterval(updatePrices, 5000);
  </script>
</body>
</html>
