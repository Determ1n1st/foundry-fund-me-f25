# 🏗️ foundry-fund-me-f25

A Solidity smart contract project that allows users to fund a contract owner in **USD-equivalent ETH**, using a **Chainlink Price Feed** for conversion. The contract ensures that only those who meet the **minimum funding requirement** can contribute, and only the **owner** can withdraw funds.  
This project is part of my smart contract security research journey.

---

## 🚀 Features

- ✅ Fund the contract with ETH ≥ $5 USD
- ✅ Uses Chainlink's **ETH/USD price feed** for conversion
- ✅ Tracks individual funders and their contributions
- ✅ Allows only the **contract owner** to withdraw funds
- ✅ Configurable to run on **Sepolia**, **mainnet**, or **Anvil** (local fork)

---

## ⚙️ Technologies Used

- [Solidity](https://soliditylang.org/)
- [Foundry](https://book.getfoundry.sh/)
- [Chainlink](https://chain.link/)
- [Sepolia Testnet](https://sepolia.dev/)
- [GitHub Actions](https://docs.github.com/en/actions)

---

## 📂 Directory Structure

```
foundry-fund-me-f25/
├── lib/                    # Dependencies (via forge install)
├── script/                 # Deployment and interaction scripts
│   ├── DeployFundMe.s.sol
│   ├── HelperConfig.s.sol
│   └── Interactions.s.sol
├── src/                    # Solidity contracts
│   ├── FundMe.sol
│   └── PriceConverter.sol
├── test/                   # Test suite
│   ├── integration/
│   │   └── FundMeTestIntegration.t.sol
│   └── unit/
│       └── FundMeTest.t.sol
├── mock/                   # Mock contracts
│   └── MockV3Aggregator.sol
├── foundry.toml            # Foundry configuration file
└── README.md               # This file
```

---

## 🛠️ Getting Started

### Prerequisites

- [Foundry](https://book.getfoundry.sh/getting-started/installation) installed  
- [Git](https://git-scm.com/)
- Environment variable for Sepolia RPC URL

### 1. Clone the repository

```bash
git clone https://github.com/Determ1n1st/foundry-fund-me-f25.git
cd foundry-fund-me-f25
```

### 2. Set environment variable

Create a `.env` file and add your Sepolia RPC URL and private key:

```env
SEPOLIA_RPC_URL=https://sepolia.infura.io/v3/your_project_id
PRIVATE_KEY=your_private_key
```

### 3. Install dependencies

```bash
forge install
```

### 4. Run tests

```bash
forge test
```

### 5. Deploy locally (Anvil)

```bash
anvil
# In a new terminal
forge script script/DeployFundMe.s.sol --rpc-url http://127.0.0.1:8545 --private-key <PRIVATE_KEY> --broadcast
```

### 6. Deploy to Sepolia

```bash
forge script script/DeployFundMe.s.sol --rpc-url $SEPOLIA_RPC_URL --private-key $PRIVATE_KEY --broadcast --verify
```

---

## 🧪 Testing with Mocks

On local chains like **Anvil**, the script uses a **MockV3Aggregator** instead of a real Chainlink price feed.  
This is handled via the `HelperConfig.s.sol` script and set automatically based on `block.chainid`.

---

## 🔐 Why This Project?

This project is a hands-on implementation to better understand:

- Security implications in funding logic
- Handling owner-only permissions
- Managing price feeds and mocks
- Preparing for smart contract audits

---

## 📜 License

[MIT](LICENSE)
