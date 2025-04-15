
# 🔥 Assignment 2.2 – Solana Hello World (Rust)

This project documents the full process of building, debugging, and deploying a minimal Solana smart contract using **Rust** on **Devnet**. The contract simply logs `"Hello, Solana!"` and served as a hands-on guide for working with the Solana toolchain, Rust compilation targets, and CLI deployment.

---

## 🧠 What I Did – Step-by-Step

### ✅ 1. Installed the Solana CLI

Installed using the official script:
```bash
sh -c "$(curl -sSfL https://release.solana.com/stable/install)"
```
Then added Solana CLI to PATH:
```bash
export PATH="$HOME/.local/share/solana/install/active_release/bin:$PATH"
```
Verified with:
```bash
solana --version
```

---

### ✅ 2. Configured Solana to Devnet

```bash
solana config set --url https://api.devnet.solana.com
```

---

### ✅ 3. Generated a New Wallet & Airdropped SOL

```bash
solana-keygen new
solana address       # Saved this for future use
solana airdrop 2     # On Devnet
```

---

### ✅ 4. Created and Configured a New Rust Smart Contract

Created a fresh Rust library project:
```bash
cargo new --lib hello_solana
cd hello_solana
```

Updated `Cargo.toml`:

```toml
[package]
name = "hello_solana"
version = "0.1.0"
edition = "2021"

[lib]
crate-type = ["cdylib"]

[dependencies]
solana-program = "1.18.2"
```

---

### ✅ 5. Wrote a Minimal Smart Contract

**`src/lib.rs`:**

```rust
use solana_program::{
    account_info::AccountInfo,
    entrypoint,
    entrypoint::ProgramResult,
    pubkey::Pubkey,
    msg,
};

entrypoint!(process_instruction);
fn process_instruction(
    _program_id: &Pubkey,
    _accounts: &[AccountInfo],
    _instruction_data: &[u8],
) -> ProgramResult {
    msg!("Hello, Solana!");
    Ok(())
}
```

---


### ✅ 6. Deployed the Program to Devnet

```bash
solana program deploy ./target/deploy/hello_solana.so
```

Received output:
```
Program Id: <PASTE_YOUR_PROGRAM_ID_HERE>
```

Saved this Program ID as my deployed contract address.

---

## 📬 My Wallet

```bash
solana address
# Output: <YOUR WALLET ADDRESS>


---

## 📌 Program ID

```bash
# From successful deploy:
Program Id: <YOUR PROGRAM ID>
```
DEMOS
[Blockchain Technologies.pdf](https://github.com/user-attachments/files/19754488/Blockchain.Technologies.pdf)


---
