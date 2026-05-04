# 📡 Cloudflare WARP SSH Safe Setup (TKU)

## 📌 Overview

By installing Cloudflare WARP on our Linux server, we can route all traffic through the secure WARP tunnel. However, when you enable WARP while connected via SSH, the connection may drop. Preventing this is simple: exclude your own IP from the tunnel.

---

## ⚙️ Supported Systems

- Ubuntu  
- Debian-based distributions  

---

## 🚀 Installation

### 1️⃣ Add Cloudflare GPG key and repository

```bash
curl -fsSL https://pkg.cloudflareclient.com/pubkey.gpg | sudo gpg --yes --dearmor --output /usr/share/keyrings/cloudflare-warp-archive-keyring.gpg &&
echo "deb [signed-by=/usr/share/keyrings/cloudflare-warp-archive-keyring.gpg] https://pkg.cloudflareclient.com/ $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/cloudflare-client.list &&
sudo apt-get update && sudo apt-get install cloudflare-warp -y &&
warp-cli registration new &&
warp-cli mode warp+doh
      
```

---

## 2️⃣ Prevent SSH Disconnect (IMPORTANT)

Before enabling WARP, exclude your current access IP:

```bash
warp-cli tunnel ip add YOUR_HOME_IP_ADDRESS
```

Replace:

```
YOUR_HOME_IP_ADDRESS → your actual public IP address
```

---

## 3️⃣ Connect WARP

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


## ✨ Credits

TKU (The Keyboard Users)  
© 2026
