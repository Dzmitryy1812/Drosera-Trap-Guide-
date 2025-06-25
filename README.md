## 🪤 Drosera Trap Deployment Guide (Get Sergeant Role)

This guide helps you deploy your own trap in [Drosera](https://www.drosera.io/) to qualify for the **Sergeant** role.

---

### 🔧 System Requirements

* 2 CPU Cores
* 4 GB RAM
* 20 GB Disk Space
* VPS (Recommended: [Get a \$5 VPS](https://www.vultr.com/))
* [Holesky ETH RPC](https://www.alchemy.com/) via Alchemy or QuickNode
* Fund wallet with Holesky ETH

---

### ⚙️ Step 1: Install Dependencies

```bash
# Drosera CLI
curl -L https://app.drosera.io/install | bash
source ~/.bashrc
droseraup

# Foundry CLI
curl -L https://foundry.paradigm.xyz | bash
source ~/.bashrc
foundryup

# Bun JS runtime
curl -fsSL https://bun.sh/install | bash
source ~/.bashrc
```

---

### 🧪 Step 2: Initialize Your Trap Project

```bash
mkdir my-drosera-trap && cd my-drosera-trap

# Replace with your GitHub email and username
git config --global user.email "your@email.com"
git config --global user.name "YourUsername"

# Initialize with Drosera Foundry template
forge init -t drosera-network/trap-foundry-template

# Install JS deps (required for drosera CLI)
bun install
```

---

### ✍️ Step 3: Add Your Trap

1. Move to your trap directory:

   ```bash
   cd my-drosera-trap
   ```

2. Create a new file:

   ```bash
   nano src/Trap.sol
   ```

3. Paste your **Trap smart contract** into `Trap.sol`.
   *Note: Keep it under 2 functions to comply with guidelines.*

---

### ⚙️ Step 4: Edit `drosera.toml` Config

```bash
nano drosera.toml
```

Modify the following fields:

```toml
path = "out/Trap.sol/Trap.json"
response_contract = "0xYourSmartContractAddress"
response_function = "respondWithDiscordName(string)"
```

---

### 🚀 Step 5: Deploy the Trap

1. Build the contract:

   ```bash
   forge build
   ```

2. Dry-run to test:

   ```bash
   drosera dryrun
   ```

3. Deploy:

   ```bash
   DROSERA_PRIVATE_KEY=your_private_key drosera apply
   ```

Make sure your wallet is funded with Holesky ETH.

When prompted, type `ofc` and press `Enter`.

---

### ✅ Done!

Once deployed, your trap will be live on Drosera and connected to your operator. You can now:

* Share your deployed trap in the Drosera Discord
* Request the **Sergeant** role after review

---

### 📌 Notes

* Your `respondWithDiscordName(string)` function should emit or store the sender's Discord name.
* Join the [Drosera Discord](https://discord.gg/drosera) for help and updates.

---
