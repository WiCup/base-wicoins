# **Wicoins Project**

![Wicoins Project](https://res.cloudinary.com/gregoryinnovo/image/upload/v1728860743/foodhy/a3y5xbqiielugirsxy8h.png)

🚀 **Wicoin** is a smart contract project and full application (backend + frontend) developed to manage the issuance of Wicoin tokens and provide **recharge** functionality over the **Sepolia Base** network. This project uses **Solidity** for the contract, **Node.js** for the backend, and a **simple frontend** in HTML/JavaScript to interact with the contract.

## **Index**

- [Project Description](#project-description)
- [Features](#features)
- [Requirements](#requirements)
- [Installation](#installation)
- [Use](#use)
- [Project Structure](#project-structure)
- [Useful Commands](#useful-commands)
- [Contributions](#contributions)
- [License](#license)

---

## **Project Description**

This project aims to provide a simple solution to manage tokens using **Wicoin** and allow users to top up their balances from the frontend. All logic is deployed on the **Base Sepolia** network, an Ethereum-compatible testnet network.

The backend manages transactions on the blockchain and communicates with the smart contract, while the frontend allows users to easily recharge.

---

## **Features**

- Smart contract for issuing Wicoin tokens in Solidity.
- Recharge function available in the backend that interacts with the blockchain.
- Simple frontend interface to recharge.
- Secure connection using **dotenv** to manage private keys and sensitive settings.
- Compatible with the **Sepolia Base** network for free testing.

---

## **Requirements**

- **Node.js** and **npm** installed. You can verify with:
  ```bash
  node -v
  npm -v
  ```
- **MetaMask** configured with the Sepolia Base network.
- **ETH test in Sepolia**. You can get it from a [Sepolia Faucet](https://sepoliafaucet.com).
- **Hardhat** to compile and deploy smart contracts:
  ```bash
  npm install --save-dev hardhat
  ```

---

## **Installation**

1. **Clone the repository**:

   ```bash
   git clone https://github.com/your-user/base-wicoins.git
   cd base-wicoins
   ```

2. **Install the dependencies**:

   ```bash
   npm install
   ```

3. **Set environment variables**:
   Create a **`.env`** file in the project root with the following content:

   ```bash
   PRIVATE_KEY=your_private_key
   SEPOLIA_RPC_URL=https://sepolia.base.org
   CONTRACT_ADDRESS=your_contract_address
   ```

4. **Compile the smart contract**:

   ```bash
   npx hardhat compile
   ```

5. **Deploy the contract on the Sepolia network**:
   Run the deployment script command or run the following command:

   ```bash
   npx hardhat run scripts/deploy.js --network sepolia
   ```

---

## **Usage**

1. **Create the `.env` file**:

   - Make sure to create a `.env` file in the backend folder from the example file `.env.example`.
   - This file should contain the following necessary credentials:

     **Example of `.env` content:**

     ```bash
     PRIVATE_KEY=your_private_key
     SEPOLIA_RPC_URL=your_infura_api_key
     CONTRACT_ADDRESS=your_contract_address
     ```

2. **Install necessary dependencies**:
   If you haven't already, install the backend and contract dependencies:

   ```bash
   cd backend-wicoins
   npm install
   ```

3. **Start the Backend**:
   Start the backend server using the following command:

   ```bash
   node backend-wicoins/main.js
   ```

4. **Open the Frontend**:

   - Open the `frontend-wicoins/index.html` file in your web browser.
   - Use the interface to enter an Ethereum address and the amount you want to recharge.
   - Click the corresponding button to send the transaction.

5. **Test the Endpoint with a REST API Client (like Postman)**:

   - If you prefer, you can also manually test the endpoint using Postman or any other REST API client.

     **Request Configuration:**

     - **Method:** `POST`
     - **URL:** `http://localhost:3000/recharge`
     - **Body:** (in JSON format)
       ```json
       {
         "account": "YOUR_ETHEREUM_ADDRESS",
         "amount": 50000
       }
       ```
     - **Expected response:**
       ```json
       {
         "status": "Success",
         "txHash": "0xe1c7247894423421347823abDHBSJKBKkjjkhbk99d74cc1b9269fda12e408f28e08b"
       }
       ```

6. **Verify Transactions on the Blockchain**:
   - Once you complete a recharge, you can verify the transaction on the **Sepolia** network.
   - Visit the [Sepolia Etherscan explorer](https://sepolia.etherscan.io) and enter the **transaction hash** to confirm its status.

---

## **Project Structure**

```plaintext
wicoin-project/
│
├── backend-wicoins/         # Backend code in Node.js
│   ├── .env                 # Environment variables
│   ├── main.js              # Backend main file
│   ├── package.json         # Backend dependencies
│   └── package-lock.json    # Version locking
│
├── frontend-wicoins/        # Frontend interface for the example project
│   └── index.html           # Main HTML page for the frontend
│
├── wicoins-contracts/       # Smart contracts and deployment scripts
│   ├── artifacts/           # Artifacts generated by Hardhat
│   ├── cache/               # Hardhat cache
│   ├── contracts/           # Solidity contracts
│   ├── ignition/            # Advanced deployment tools
│   ├── node_modules/        # Project dependencies
│   ├── scripts/             # Deployment and execution scripts
│   ├── test/                # Contract tests
│   ├── typechain-types/     # Types generated by TypeChain
│   ├── .env                 # Environment variables
│   ├── hardhat.config.ts    # Hardhat configuration
│   ├── package.json         # Project dependencies
│   ├── package-lock.json    # Version locking
│   ├── README.md            # Project information
│   └── tsconfig.json        # TypeScript configuration
```

---

## **Useful Commands**

- **Compile the contract**:

  ```bash
  npx hardhat compile
  ```

- **Deploy the contract**:

  ```bash
  npx hardhat run scripts/deploy.js --network sepolia
  ```

- **Start the backend**:

  ```bash
  node backend-wicoins/main.js
  ```

- **Check the account balance**:
  Add this snippet to the backend to print the balance:
  ```javascript
  const balance = await provider.getBalance(wallet.address);
  console.log(`Balance: ${ethers.formatEther(balance)} ETH`);
  ```

---

## **License**

Private license. All rights reserved.
