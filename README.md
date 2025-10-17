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
ssh root@your_vps_ip
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
## 💥 Get Your RL Swarm Node Up & Running (Linux/Mac)

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
💠 Now it will promt you to login: Follow: 1️⃣ How to Login or access http://localhost:3000/ in VPS? 📶

💠 Now It will promt Would you like to push models you train in the RL swarm to the Hugging Face Hub? [y/N] Enter N

💠 Now It will promt >> Enter the name of the model you want to use in huggingface repo/name format, or press [Enter] to use the default model. press Enter & get defalut model:

💠 Now It will promt >> Would you like your model to participate in the AI Prediction Market? [Y/n] Enter Y

🛌 Step 6 – Detach from the screen session (Optional)

Keep the node running even if you close the terminal:

Press Ctrl + A, then D.

👉 USE THIS FOR BACKUP:
```bash

[ -f backup.sh ] && rm backup.sh; curl -sSL -O https://raw.githubusercontent.com/AbhiEBA/gensyn1/main/backup.sh && chmod +x backup.sh && ./backup.sh
```
# 🧰 **FAQ & Troubleshoot Guide**

### 🌍 **How to Access Node Dashboard (`http://localhost:3000/`) from VPS**

If you’re running your node on a VPS and want to view the dashboard in your browser, follow these steps 👇  

---

### 🔹 **1. Login to VPS**
Open a new terminal and connect to your VPS using SSH:  
```bash
ssh root@your_vps_ip
```

🔹 2. Allow Incoming Connections

Enable the required ports for SSH and your node dashboard:

```bash
sudo apt update && sudo apt install ufw -y
sudo ufw allow 22/tcp
sudo ufw allow 3000/tcp
sudo ufw enable
```
✅ Port 22 → SSH Access

✅ Port 3000 → Node Dashboard

🔹 3. Install Cloudflared (Cloudflare Tunnel)

Install Cloudflare Tunnel to securely expose your local dashboard.

```bash
wget -q https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb
sudo dpkg -i cloudflared-linux-amd64.deb
```
Check version:
```bash
cloudflared --version
```

🔹 4. Run Secure Tunnel

Start the tunnel to expose your local dashboard:

```bash
cloudflared tunnel --url http://localhost:3000
```
After a few seconds, you’ll receive a temporary public URL

example - https://random-name.trycloudflare.com

<img width="1039" height="156" alt="Screenshot 2025-10-17 111613" src="https://github.com/user-attachments/assets/7c9508de-5737-43ad-9799-52cdfb5e6337" />

Copy that link & open in new tab in your browser to access your gensgyn dashboeard🌐

# 🧩 **Node Upgrade & Security Patch (v0.6.3)**

### ⚠️ **Important Notice**
A new security update **v0.6.3** has been released.  
Make sure to **upgrade your node** to stay fully compatible and secure.

---

### 🔧 **Upgrade Steps**

#### 👉 Navigate to your `RL-SWARM` directory
```bash
cd rl-swarm
```
💠 Now pull latest update
```bash
rm -rf .venv && git pull && python3 -m venv .venv && source .venv/bin/activate
```

💡 If you have uncommitted changes

Run this command before pulling updates:

```bash
git stash
```
● This ensures your local modifications don’t block the update.
























  




