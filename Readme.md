# Solana Favorites Program

A Rust & Anchor-based Solana smart contract to set and store a user's favorite number, color, and hobbies on-chain.

---

## 🧰 Tech Stack

- **Solana** — High-performance blockchain for decentralized apps  
- **Rust** — Smart contract (program) language  
- **Anchor** — Framework for Solana program development/testing  
- **Solana CLI** — Solana blockchain command-line tools  
- **dotenv** — Manage local environment variables  

---

## ✨ Features

- Store and update a user's favorites (number, color, hobbies) on-chain  
- Derived account address based on wallet public key (using seeds)  
- Test and run on Devnet/Testnet clusters  

---

## 🚀 Getting Started

### Prerequisites

Make sure you have the following installed:

- Rust → [Install here](https://rustup.rs/)
- Solana CLI →  
  ```bash
  sh -c "$(curl -sSfL https://release.solana.com/v1.18.10/install)"
  ```
- Anchor CLI →  
  ```bash
  cargo install --git https://github.com/coral-xyz/anchor avm --locked
  avm install latest
  avm use latest
  ```
- Node.js/NPM (for JS test framework, optional)
- [Git](https://git-scm.com/)

### Clone the Repository

```bash
git clone https://github.com/yourusername/solana-favorites.git
cd solana-favorites
```

---

## 🧩 Local Setup (Testnet)

### 1. Configure Solana CLI

```bash
solana config set --url https://api.testnet.solana.com
```

### 2. Wallet Keypair Setup

If you already have a Solana wallet, you can use it.  
Otherwise, generate a new keypair:

```bash
solana-keygen new --outfile ~/.config/solana/id.json
```

Set the CLI to use this key:

```bash
solana config set --keypair ~/.config/solana/id.json
```

Check your public key:

```bash
solana address
```

### 3. Airdrop Testnet SOL

```bash
solana airdrop 2
```

### 4. Install Project Dependencies

```bash
anchor build
```
*(installs Rust dependencies and builds Solana binary)*

---

## 🛠️ Deployment

### 1. Deploy to Testnet

```bash
anchor deploy --provider.cluster testnet
```

After deployment, copy the program ID from the output.

Update this line in `programs/favorites/src/lib.rs`:
```rust
declare_id!("YOUR_DEPLOYED_PROGRAM_ID");
```

Then, in `Anchor.toml`:
```toml
[programs.testnet]
favorites = "YOUR_DEPLOYED_PROGRAM_ID"
```

### 2. Sync Keypairs

- **Do not share or commit `.keypair.json` files!**
- Each contributor should create their own wallet and configure it locally.

---

## 🧪 Running Tests

Run tests directly on the testnet:

```bash
anchor test --provider.cluster testnet
```

---

## ⚙️ Environment Configuration

Use a `.env` file to manage sensitive data.  
Add `.env` to your `.gitignore`.

Example `.env`:

```
ANCHOR_PROVIDER_URL=https://api.testnet.solana.com
WALLET_PATH=/home/username/.config/solana/id.json
PROGRAM_ID=YOUR_DEPLOYED_PROGRAM_ID
```

---

## 📁 .gitignore Recommendations

```
.env
*.keypair.json
target/
node_modules/
anchor/
test-ledger/
dist/
*.log
.vscode/
.idea/
```

---

## 🔒 Security Advice

- **Never upload wallet private keys or `.env` files**  
- Share only the public **program ID**
- Verify RPC endpoints and wallet paths before deploying or testing

---


