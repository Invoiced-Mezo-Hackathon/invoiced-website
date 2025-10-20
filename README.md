# 🧾 Invoiced

Send invoices. Get paid in Bitcoin. Stay liquid — powered by Mezo.

![Invoiced preview](./invoice-payment-app/public/preview.png)

Invoiced is a web-based invoicing and payment platform that lets freelancers and businesses create Bitcoin-denominated invoices, receive payments instantly, and access spendable cash without selling their BTC. It’s built on Mezo, a Bitcoin-backed liquidity network that issues mUSD, a stable digital dollar collateralized by Bitcoin.

---

## 🚀 Overview
Invoiced connects three layers of functionality:

- **Invoice creation and management** — generate, send, and track Bitcoin invoices.
- **Payment processing** — verify and settle BTC payments on-chain through Mezo.
- **Vault integration** — deposit Bitcoin into Mezo vaults and borrow mUSD for liquidity.

The platform is non-custodial — users stay in control of their funds at all times. Everything happens directly on-chain through smart contracts deployed to the Mezo testnet (Chain ID: 31611).

---

## 🏗️ Tech Stack

| Layer | Technology |
| --- | --- |
| Frontend | Next.js 14 (App Router) + TypeScript + Tailwind CSS |
| Smart Contracts | Solidity + Hardhat + OpenZeppelin |
| Blockchain | Mezo Testnet (BTC as gas token) |
| Backend | Next.js API Routes + Prisma + PostgreSQL |
| Integration | Mezo Passport SDK + ethers.js |
| Deployment | Vercel / Docker (optional) |

---

## ⚙️ Features

### 💼 Invoice Management
- Create invoices with client, amount, and description.
- Track invoice states: Pending, Paid, Cancelled, Disputed.
- Share unique payment links directly with clients.
- On-chain events for every action: `InvoiceCreated`, `InvoicePaid`, `InvoiceCancelled`.

### ⚡ Bitcoin Payments
- Clients pay invoices directly in BTC using Mezo Passport.
- Payments are verified and recorded on-chain.
- Instant confirmation updates via the dashboard.

### 🏦 Vault & Liquidity
- Deposit Bitcoin into Mezo Vaults securely.
- Borrow up to 90% LTV in mUSD at a fixed 1% rate.
- Repay and reclaim your BTC anytime.

### 🌍 Global, Non-Custodial, Borderless
- No middlemen or banks.
- You own your keys and control your vaults.
- Works anywhere Bitcoin does.

---

## 🧱 Project Structure
```
invoiced/
├── app/                 # Next.js App Router pages
│   ├── dashboard/       # User dashboard (invoices overview)
│   ├── invoices/        # Invoice pages
│   ├── vault/           # Vault dashboard (deposit, borrow, repay)
│   ├── pay/             # Payment interface for clients
│   └── api/             # API routes for invoices, vaults, payouts
├── contracts/           # Solidity smart contracts
│   ├── InvoiceManager.sol
│   ├── VaultManager.sol
│   └── PaymentProcessor.sol
├── lib/                 # Blockchain & Mezo utilities
├── prisma/              # Prisma schema & migrations
├── components/          # Reusable UI components
└── hardhat.config.js    # Hardhat configuration for Mezo testnet
```

---

## 🧩 Key Contracts

### `InvoiceManager.sol`
- Handles all invoice lifecycle events.
- `createInvoice()`
- `payInvoice()`
- `cancelInvoice()`
- Emits events for tracking via frontend.

### `VaultManager.sol`
- Integrates with Mezo Vaults for BTC deposits and mUSD borrowing.
- `depositBTC()`
- `borrowMUSD()`
- `repayMUSD()`
- `withdrawBTC()`

### `PaymentProcessor.sol`
- Connects invoices and vault operations.
- Handles BTC payments
- Triggers vault deposits automatically
- Acts as escrow for disputes

---

## 🔧 Setup

### Prerequisites
- Node.js ≥ 18
- PostgreSQL
- Mezo testnet account (via Mezo Passport)
- BTC testnet funds (for gas)

### Installation
```bash
git clone https://github.com/yourusername/invoiced.git
cd invoiced
npm install
cp .env.example .env
```

Fill out your `.env` with:
```bash
DATABASE_URL=postgresql://user:password@localhost:5432/invoiced
NEXT_PUBLIC_MEZO_RPC=https://rpc.test.mezo.org
NEXT_PUBLIC_CHAIN_ID=31611
```

### Run locally
```bash
npm run dev
```
Frontend will be live at `http://localhost:3000`.

---

## 🧪 Smart Contract Deployment

### Compile contracts
```bash
npx hardhat compile
```

### Deploy to Mezo testnet
```bash
npx hardhat run scripts/deploy.js --network mezo
```

### Verify contracts
```bash
npx hardhat verify <CONTRACT_ADDRESS> --network mezo
```

---

## 🧠 Testing
```bash
npm run test
```
Includes unit tests for:
- Invoice creation and payments
- Vault lifecycle (deposit, borrow, repay)
- `PaymentProcessor` integration

---

## 🔒 Security & Best Practices
- Built with OpenZeppelin libraries
- Non-custodial architecture — users hold keys
- Smart contracts emit all state changes for transparency
- Rate limits and input validation for backend APIs

---

## 🌍 Demo Flow
1. Freelancer creates invoice → client receives payment link.
2. Client pays in BTC → payment confirmed on Mezo testnet.
3. Freelancer deposits BTC → borrows mUSD for liquidity.
4. Freelancer repays loan → reclaims full BTC value.

---

## 📚 Documentation
- Contracts: `/contracts`
- API routes: `/app/api`
- Frontend: `/app`
- Database schema: `/prisma/schema.prisma`

---

## 👥 Contributors
- Janice Gathoga
- Tevin Issac
- Zara Gathoni

---

## 💡 Vision
Invoiced is building a bridge between freelancers and the Bitcoin economy — one invoice at a time. By integrating Mezo’s liquidity layer, we’re making Bitcoin not just a store of value, but a tool for real work.

---

## 🧠 License
MIT © 2025 Invoiced
