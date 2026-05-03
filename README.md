# 📡 Cloudflare WARP SSH Safe Setup (TKU)

## 📌 Overview

Cloudflare WARP allows you to securely route all server traffic through an encrypted tunnel.

However, enabling WARP while connected via SSH can instantly drop your active session.

This repository provides a clean and safe solution:

- ✔ Install Cloudflare WARP on Linux servers  
- ✔ Properly configure the client  
- ✔ Prevent SSH disconnect using IP exclusion  

---

## ⚙️ Supported Systems

- Ubuntu  
- Debian-based distributions  

---

## 🚀 Installation

### 1️⃣ Add Cloudflare GPG key and repository

```bash
curl -fsSL https://pkg.cloudflareclient.com/pubkey.gpg \
| sudo gpg --yes --dearmor \
--output /usr/share/keyrings/cloudflare-warp-archive-keyring.gpg
```

```bash
echo "deb [signed-by=/usr/share/keyrings/cloudflare-warp-archive-keyring.gpg] https://pkg.cloudflareclient.com/ $(lsb_release -cs) main" \
| sudo tee /etc/apt/sources.list.d/cloudflare-client.list
```

---

### 2️⃣ Install WARP client

```bash
sudo apt-get update
sudo apt-get install cloudflare-warp -y
```

---

### 3️⃣ Register and configure

```bash
warp-cli registration new
warp-cli mode warp+doh
```

---

## 🛡️ Prevent SSH Disconnect (IMPORTANT)

Before enabling WARP, exclude your current access IP:

```bash
warp-cli tunnel ip add YOUR_HOME_IP_ADDRESS
```

Replace:

```
YOUR_HOME_IP_ADDRESS → your actual public IP address
```

---

## 🔌 Connect WARP

```bash
warp-cli connect
```

---

## 📊 Check Status

```bash
warp-cli status
```

---

## 📚 Official Documentation

https://developers.cloudflare.com/warp-client/get-started/linux/

---

## 🧪 Example Use Cases

- Secure outbound traffic on VPS  
- Hide origin IP  
- Add lightweight privacy layer  
- Combine with reverse proxies  

---

## 📬 Contact

Email: glitchbey@proton.me  

---

## 🧾 License

MIT License — free to use, modify, and distribute.

---

## ✨ Credits

TKU (The Keyboard Users)  
© 2026
