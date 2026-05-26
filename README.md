

---

# circle-usdc-transfer-demo

A beginner-friendly demo for creating and transferring USDC between Circle developer-controlled wallets entirely from the backend using TypeScript and the Circle API on Ethereum Sepolia testnet.

---

## What This Does

- Creates two smart contract wallets programmatically via Circle's API
- Funds Wallet A from Circle's testnet faucet
- Transfers USDC from Wallet A to Wallet B from the backend, no frontend, no user approval

---

## Prerequisites

- Node.js installed on your machine
- A Circle developer account, sign up at https://console.circle.com/signin
- VS Code or any code editor

---

## Setup

### 1. Clone the repository

```bash
git clone https://github.com/Prudentdev-xyz/circle-usdc-transfer-demo.git
cd circle-usdc-transfer-demo
```

### 2. Install dependencies

```bash
npm i
```

### 3. Create your `.env` file at the root of the project

```
CIRCLE_API_KEY=
CIRCLE_ENTITY_SECRET=
WALLET_A_ID=
WALLET_B_ADDRESS=
USDC_ID=
```

---

## Steps

### Generate your entity secret

```bash
npx tsx src/generate-secret.ts
```

Copy the output and paste it next to `CIRCLE_ENTITY_SECRET=` in your `.env` file.

### Register the entity secret

```bash
npx tsx src/register-secret.ts
```

This generates two recovery files at the root of your project. Keep them safe and never push them to GitHub.

### Create two smart contract wallets

```bash
npx tsx src/wallet.ts
```

Copy Wallet A's ID into `WALLET_A_ID=` and Wallet B's address into `WALLET_B_ADDRESS=` in your `.env` file. Then set your USDC token ID:

```
USDC_ID=5797fbd6-3795-519d-84ca-ec4c5f80c3b1
```

### Fund Wallet A

Visit https://console.circle.com/faucet/circle-wallet, enter Wallet A's ID, select USDC and ETH Sepolia, then click **Send tokens**.

### Transfer USDC from Wallet A to Wallet B

```bash
npx tsx src/transfer.ts
```

A transaction hash will be printed in your terminal when complete.

---

## Verify the Transaction

Go to https://sepolia.etherscan.io and search your transaction hash to confirm the transfer on-chain.

---

## Important

Never push your `.env` file or recovery files to GitHub. Make sure your `.gitignore` includes:

```
node_modules/
.env
```

---

## Full Article

Read the full technical walkthrough here — *https://medium.com/@prudenttalks/how-i-moved-usdc-between-two-smart-contract-wallets-from-the-backend-using-circles-api-530077172201*

---
