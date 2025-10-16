# <img width="30" height="-30" alt="image" src="https://github.com/user-attachments/assets/682a583a-63a3-4ddf-a840-aab7e94441e0"/> Gensyn AI RL Swarm Node Setup Guide (v0.4.3)

## 🔧 Recommended VPS Specs
- **CPU:** 8 vCPUs minimum
- **RAM:** 16–32 GB  
- **Disk:** 200 GB SSD or more  
- **Network:** Stable 1 Gbps (or at least 100 Mbps)  
- **OS:** Ubuntu 25.04 recommended  

> ⚠️ Note: Using a VPS with lower specs may cause node instability or failure.

## 💻 Login to VPS
Log in to your VPS using SSH:  
```bash
ssh username@your_vps_ip
```
Replace username with your VPS username (usually root) and your_vps_ip with your server’s IP address.

## 📦 Prerequisites
1. Update System Packages
```bash
sudo apt update && sudo apt upgrade -y
```
2. Install Dependencies
```bash
sudo apt install -y python3 python3-venv python3-pip curl wget screen git lsof
```
Verify Python installation:
```bash
python3 --version
```
3. Install Node.js, npm, & Yarn
```bash
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt update
sudo apt install -y nodejs
```
Install Yarn:
```bash
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list > /dev/null
sudo apt update
sudo apt install -y yarn
```
Verify installations:
```bash
node -v
npm -v
yarn -v
```
## 🚀 Get Your RL Swarm Node Up & Running (Linux/Mac)

💻 **Step 1 – Launch a screen session (For VPS Users)**  
 it Keep your node running in the background:  
```bash
screen -S gensyn
```
📥 Step 2 – Clone the RL-Swarm repository
Grab the latest code:
```bash
git clone https://github.com/gensyn-ai/rl-swarm.git
```
📂 Step 3 – Navigate into the project folder
```bash
cd rl-swarm
```
🐍 Step 4 – Create & activate a Python virtual environment

Isolate dependencies for smooth running:
```bash
python3 -m venv .venv
source .venv/bin/activate
```
⚡ Step 5 – Start your Swarm Node

Kick off the node and let it join the swarm:
```bash
./run_rl_swarm.sh
```
🛌 Step 6 – Detach from the screen session (Optional)

Keep the node running even if you close the terminal:

Press Ctrl + A, then D.

👉 USE THIS FOR BACKUP:
```bash

[ -f backup.sh ] && rm backup.sh; curl -sSL -O https://raw.githubusercontent.com/AbhiEBA/gensyn1/main/backup.sh && chmod +x backup.sh && ./backup.sh
```


















  




