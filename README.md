# 🎁 Gift List Project

This project implements a **Merkle Tree-based gift verification system**, inspired by the blockchain concept of minimal data verification.

---

## 📌 Overview

The goal is to allow a server to verify if a given name is on a predefined gift list using only a **single 32-byte Merkle Root** stored on the server — without storing the entire list.

The client proves membership by sending a **Merkle Proof** for their name, which the server verifies cryptographically.

---

## ✅ What I Added / Implemented

### 🌲 Merkle Tree Construction

- Created a `MerkleTree` class that hashes and organizes the list of names (`niceList.json`) into a Merkle Tree.
- Enables efficient generation of Merkle Proofs.

### 🧠 Client Logic (`client/index.js`)

- The client builds the Merkle Tree locally.
- Generates a Merkle Proof for a specific name.
- Sends the proof and the name to the server for verification.

### 🖥️ Server Logic (`server/index.js`)

- The server holds a **hardcoded Merkle Root** representing the gift list.
- Verifies the Merkle Proof for the provided name against the stored root.
- Responds with a gift message if the name is valid.

### 🔐 Proof Verification (`utils/verifyProof.js`)

- Cryptographic verification function that:
  - Rebuilds the path from the leaf node (hashed name) to the Merkle Root.
  - Uses the proof sent by the client to confirm membership.

### 🗃️ Hardcoded Merkle Root

- Precomputed the Merkle Root from the full `niceList.json`.
- Hardcoded it in the server to simulate **minimal on-server storage**.

---

## 🚀 How to Run

1. Clone the repo and install dependencies:

   ```bash
   npm install
   ```

2. Start the server:

   ```bash
   node server/index.js
   ```

3. Run the client script (edit the name in `client/index.js` if desired):

   ```bash
   node client/index.js
   ```

4. The client sends a proof to the server to verify if the name is on the gift list.
5. The server responds with either a gift message or a rejection.

---

## 📁 Project Structure

```
project-root/
├── client/          # Proves membership with Merkle Proofs
├── server/          # Verifies proofs against the Merkle Root
├── utils/           # Utilities and logic
│   ├── niceList.json      # List of names eligible for gifts
│   ├── MerkleTree.js      # Merkle Tree implementation
│   ├── verifyProof.js     # Server-side proof verification
│   └── example.js         # Demo: roots, proofs, and verification
```

---

## 📝 Notes

- This project showcases how **blockchain-inspired data structures** can optimize verification without storing entire datasets.
- Merkle Tree and Proof system ensures:
  - ✅ Minimal data transfer
  - 🔒 Secure verification
- Useful for **decentralized** and **privacy-sensitive** applications.
