# 🚀 Deploying a Java Gradle Application on DigitalOcean

## 📌 Project Description

This project demonstrates how to:

- Create and configure a DigitalOcean Droplet
- Apply Linux security best practices
- Install Java (OpenJDK 17)
- Build a Java Gradle application
- Deploy and run the application on a Linux server
- Verify running processes and open ports

---

## 🛠 Technologies Used

- DigitalOcean
- Ubuntu Linux
- Java 17 (OpenJDK)
- Gradle
- SSH
- SCP
- Netstat / ss

---

# 🖥 STEP 1: Create DigitalOcean Droplet

1. Log in to DigitalOcean.
2. Create a new Ubuntu Droplet.
3. Add your SSH key during setup (recommended).
4. Copy the server IP address.

---

# 🔐 STEP 2: SSH into the Droplet

```bash
ssh root@209.97.187.212
