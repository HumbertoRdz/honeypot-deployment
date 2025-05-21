# Honeypot Deployment on AWS (T-Pot)

This walkthrough shows how to deploy the T-Pot honeypot platform on AWS using a Debian-based EC2 instance. It includes setup, SSH troubleshooting, port configuration, and final access to the web interface.

---

# 📺 Video Tutorial

> [Install Honeypot in AWS (in Spanish)](https://www.youtube.com/watch?v=IXTxLEMi5EI)

---

# 🚀 Step-by-Step Guide

## 1. EC2 Instance Setup

- Choose a Debian 11 Support by SupportedImages | AMI and c4.xlarge instance or better.
- Create a security group that allows:
  - Port 22 (SSH) from "My IP"
    
![Captura de pantalla 2025-05-20 204916](https://github.com/user-attachments/assets/575cded3-10cb-4765-a686-c48af1a5a7b0)

---

## 2. SSH Key Pair

- Choose an existing key pair or create a new one (save the `.pem` file securely).
  
![Captura de pantalla 2025-05-20 204933](https://github.com/user-attachments/assets/c6b0f595-b2e2-4b96-8636-11e6e1abaf0a)

---

## 3. Storage

- Set at least **64 GiB** of SSD (gp3 or gp2).

![Captura de pantalla 2025-05-20 204945](https://github.com/user-attachments/assets/927b9085-9dad-42ba-a7c9-e31b8320e80b)


---

## 4. SSH Access Notes

If you try to SSH **immediately after launching**, you may get:
ssh: connect to host ... port 22: Connection refused 




> This happens because the instance is still initializing. Wait 1–2 minutes and try again.

![Captura de pantalla 2025-05-20 205006](https://github.com/user-attachments/assets/17060a32-a5fb-4709-a09a-07a7e60878ad)

If you see a **Permission denied (publickey)** error like this:

![Captura de pantalla 2025-05-20 205111](https://github.com/user-attachments/assets/8fb48de0-edd8-451a-8cb0-d8a7f7603227)


## 🔧 Fix `.pem` file permissions (on Windows):
1. Right-click the `.pem` file → Properties → Security → Advanced.
2. Click **Disable inheritance**.
3. Click **Add** → **Select a principal** → enter your Windows username.
4. Set **Full Control** → OK → Apply.
5. Retry the SSH connection.

---

## 5. Connect and Prepare Environment

```bash
sudo apt-get update
sudo apt-get install git
git clone https://github.com/telekom-security/tpotce
cd tpotce
```
![Captura de pantalla 2025-05-20 205401](https://github.com/user-attachments/assets/c5f5abce-c8ed-49e5-a793-b3ecc38cdc37)

![Captura de pantalla 2025-05-20 205416](https://github.com/user-attachments/assets/38b8c9cb-1b7d-4511-8bfe-df38eede5c86)

## 6. Run the Installer
```bash
sudo ./install.sh
```
Choose H for T-Pot Standard, and set up the web user credentials.

![Captura de pantalla 2025-05-20 205432](https://github.com/user-attachments/assets/380df8f8-50d8-406d-bded-22d82a4d3215)

![image](https://github.com/user-attachments/assets/12169cec-acb9-467f-979c-d192c048fd05)

## 7. Reboot
Once the setup finishes, reboot:

```bash
sudo reboot
```
## 8. Update Security Group Rules
To access the web interface:

Allow inbound traffic on port 4297 fo "My IP"
And allow all inbound traffic from ports 0-64000

![Captura de pantalla 2025-05-20 205612](https://github.com/user-attachments/assets/403e21e7-8ba8-4a4e-86b7-a66c72df9d32)


## 9. Access the Web UI
Go to https://YOUR-EC2-IP:4297. You may get a certificate warning:

![Captura de pantalla 2025-05-20 205649](https://github.com/user-attachments/assets/6b437205-c4ca-4dea-a2e9-3ce7fe63e323)


Click Proceed anyway.

## 10. T-Pot Dashboard
If everything went well, you should see the T-Pot 24
![Captura de pantalla 2025-05-20 205700](https://github.com/user-attachments/assets/619a0fe5-3a59-4da3-849e-48ee3c81bf06)










