<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>DApp Wallet Connect</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <div class="container">
    <h1>Connect Your Wallet</h1>
    <button id="connectWalletBtn">Connect Wallet</button>
    <div id="accountInfo" class="hidden">
      <h2>Connected Account:</h2>
      <p id="accountAddress"></p>
    </div>
  </div>
  <script src="app.js"></script>
</body>
</html>
body {
  font-family: Arial, sans-serif;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  margin: 0;
  background-color: #f0f0f0;
}

.container {
  text-align: center;
}

button {
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
}

.hidden {
  display: none;
}
import WalletConnect from "@walletconnect/web3-provider";
import Web3 from "web3";

// Initialize WalletConnect
const provider = new WalletConnect({
  infuraId: "YOUR_INFURA_PROJECT_ID", // Replace with your Infura Project ID
});

const web3 = new Web3(provider);

// Function to connect wallet
async function connectWallet() {
  if (!provider.connected) {
    await provider.enable();
  }
  const accounts = await web3.eth.getAccounts();
  document.getElementById('accountAddress').textContent = accounts[0];
  document.getElementById('accountInfo').classList.remove('hidden');
}

// Event listener for the connect button
document.getElementById('connectWalletBtn').addEventListener('click', connectWallet);
npm init -y
npm install @walletconnect/web3-provider web3
npx live-server
