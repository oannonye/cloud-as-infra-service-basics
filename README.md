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
5. Setup firewall to allow only ssh traffic on port 22

---

# 🔐 STEP 2: SSH into the Droplet

```bash
ssh root@<Droplet public ip>
```
## 🚀 Deployment Steps (3–10)

### Step 3: Update Server & Install Java

```bash
apt update
apt install openjdk-17-jre-headless -y
java -version
```

### Step 4: Create a New Linux User and add to sudo group (Security Best Practice)

```bash
adduser $USER
usermod -aG sudo $USER

```

### Step 5: Configure SSH Access for New User

```bash
su - $USER
mkdir ~/.ssh
sudo vim ~/.ssh/authorized_keys
```

Paste your local machine public SSH key into the `authorized_keys` file.

Test SSH login:

```bash
ssh $USER@<Droplet public ip>
```

### Step 6: Clone and Build Application (Local Machine)

```bash
git clone https://gitlab.com/twn-devops-bootcamp/latest/05-cloud/java-react-example
cd java-react-example
gradle build
```

The JAR file will be generated at:

```
build/libs/java-react-example.jar
```

### Step 7: Transfer JAR File to Droplet

```bash
scp build/libs/java-react-example.jar $USER@<Droplet public ip>:/home/$USER
```

### Step 8: Run Application on Droplet

```bash
java -jar java-react-example.jar
```

Run in background:

```bash
nohup java -jar java-react-example.jar &
```

### Step 9: Verify Application is Running

```bash
ps aux | grep java
netstat -lpnt
```

If `netstat` is not installed:

```bash
sudo apt install net-tools -y
```

### Step 10: Access Application

Open in browser:

```
http://<Droplet public ip>:<application-port>
```

Replace `<application-port>` with the port shown in the netstat or ss output.
