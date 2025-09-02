# 🚀 Foundry Learning Cheat Sheet  

**Foundry** is a blazing fast, portable, and modular toolkit for Ethereum application development written in Rust.  

It is used for **developing, testing, deploying, and interacting** with smart contracts.  

---

## 📦 Foundry Components  

- **Forge** → Testing & build framework (like Hardhat/Truffle).  
- **Cast** → Interact with contracts & chain data.  
- **Anvil** → Local Ethereum node (like Ganache/Hardhat Network).  
- **Chisel** → Solidity REPL for prototyping.  


---

## 🛠️ Core Commands  

### 🔨 Build Contracts  
```bash
forge build

🧪 Run Tests
forge test

🎨 Format Code
forge fmt

⛽ Gas Snapshot
forge snapshot

🌐 Start Local Blockchain
anvil


👉 Runs local node at http://127.0.0.1:8545 with 10 funded accounts.

📤 Deploy Contract
forge create ContractName \
  --rpc-url http://127.0.0.1:8545 \
  --private-key <YOUR_PRIVATE_KEY>

📡 Interacting with Smart Contracts (Cast)
✍️ Write (Send TX)
cast send <CONTRACT_ADDRESS> "store(uint256)" 123 \
  --rpc-url http://127.0.0.1:8545 \
  --private-key <YOUR_PRIVATE_KEY>

📖 Read (Call Function → Hex)
cast call <CONTRACT_ADDRESS> "retrieve()" \
  --rpc-url http://127.0.0.1:8545


Output example:

0x7b

🔢 Convert Hex → Decimal
cast --to-base 0x7b dec
# Output: 123

🔐 Bonus: Secure Keystore (No raw private key)

Instead of using --private-key everywhere, store your key securely:

Import Keystore
cast wallet import myAccount --interactive


→ Enter your private key & set a password (encrypted keystore).

Use Secure Account
cast send <CONTRACT_ADDRESS> "store(uint256)" 321 \
  --rpc-url http://127.0.0.1:8545 \
  --account myAccount

Read + Convert
cast call <CONTRACT_ADDRESS> "retrieve()" --rpc-url http://127.0.0.1:8545
cast --to-base 0x141 dec   # 0x141 = 321

✅ Final Secure Workflow

anvil → start blockchain

forge build → compile contracts

forge create → deploy contract

cast send → write data (store)

cast call → read data (hex)

cast --to-base <hex> dec → decode to integer

cast wallet import + --account → secure key management
