## 🪤 Drosera Trap Deployment Guide (Get Sergeant Role)

This guide helps you deploy your own trap in [Drosera](https://www.drosera.io/) to qualify for the **Sergeant** role. If you already have an idea and a smart contract traps. 

---

### 🔧 System Requirements

* 2 CPU Cores
* 4 GB RAM
* 20 GB Disk Space
* [Holesky ETH RPC](https://www.alchemy.com/) via Alchemy or QuickNode
* Fund wallet with Holesky ETH

---
### Install Dependecies
```bash
sudo apt-get update && sudo apt-get upgrade -y
sudo apt install curl ufw iptables build-essential git wget lz4 jq make gcc nano automake autoconf tmux htop nvme-cli libgbm1 pkg-config libssl-dev libleveldb-dev tar clang bsdmainutils ncdu unzip libleveldb-dev  -y
```
### Install Docker

```bash
sudo apt update -y && sudo apt upgrade -y
for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done

sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update -y && sudo apt upgrade -y

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# Test Docker
sudo docker run hello-world
```




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
git config --global user.name "YourUsername_github"

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
path = "out/Trap.sol/Trap.json"  //(the path to your smart contract)  
response_contract = "0xYourSmartContractAddress"  // (here you need to enter the address of the smart contract that you have depolyed) 
response_function = "function(string)"  // (the function of your depolyed smart contract) 
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
![image](https://github.com/user-attachments/assets/aa3aab61-c9f7-452f-8200-e1a3da847507)

3. Deploy:

   ```bash
   DROSERA_PRIVATE_KEY=your_private_key drosera apply
   ```

Make sure your wallet is funded with Holesky ETH.

When prompted, type `ofc` and press `Enter`.

---

### ✅ Done!

Once deployed, your trap will be live on Drosera and All that remains is to connect to the operator. You can now:

* Share your deployed trap in the Drosera Discord
* Request the **Sergeant** role after review

---

### 📌 Notes

* Your `respondWithDiscordName(string)` function should emit or store the sender's Discord name.
* Join the [Drosera Discord](https://discord.gg/drosera) for help and updates.

---
