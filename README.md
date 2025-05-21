# Honeypot Deployment on AWS (T-Pot)

This walkthrough demonstrates how to deploy a honeypot using T-Pot on AWS. T-Pot is a powerful open-source honeypot platform that integrates multiple honeypot services into one.

This project is part of a video tutorial available on my YouTube channel, and includes screenshots from the installation process for visual guidance.

## 📽️ Video

Watch the full walkthrough (Spanish) on YouTube:  
[[🔗 Instalar un Honeypot (T-Pot) en AWS ](https://www.youtube.com/watch?v=IXTxLEMi5EI)]

---

## 🛠️ Technologies Used

- AWS EC2
- Ubuntu Server 20.04
- T-Pot Framework (https://github.com/telekom-security/tpotce)
- Security Groups & SSH
- Cloud-init / Shell scripting

---

## 🚀 Deployment Steps

1. **Launch an EC2 Instance**
   - Region: Choose a region near you
   - AMI: Ubuntu Server 20.04
   - Instance Type: t2.medium or higher
   - Storage: At least 64 GB
   - Open ports: `22`, `64295`, `80`, `443`, `8080`, etc. (see video)

2. **Connect via SSH**
   ```bash
   ssh -i your-key.pem ubuntu@your-ec2-ip
