# Snort-Setup

![Project Logo](https://webobjects2.cdw.com/is/image/CDW/3521758?$product-main$) 

## 🚀 Overview
Comprehensive Guide to Snort Intrusion Detection and Prevention Setup

## 🔥 Why Use Snort?
Snort is a popular, open-source Intrusion Detection and Prevention System (IDS/IPS) that monitors network traffic to spot and stop suspicious activity, keeping systems safe. This guide will help you set up and run Snort on Ubuntu.

## 🔥 How This Helps
**Real-Time Monitoring**  
Snort watches network traffic and alerts to any suspicious activity.

**Customizable Alerts**  
Rules can be tailored to detect specific threats relevant to the network.

**Community Rules**  
Regular updates help stay protected against new threats.

## 🛠️ Installation
### Step 1: Install Snort
- Open the terminal and install Snort:

   ```bash
   sudo apt-get install snort -y
   ```
- Set HOME_NET to your network (e.g., 192.168.0.0/24).
- Verify the installation by running:
   ```bash
   snort --version
   ```
   ![Description](https://raw.githubusercontent.com/itstonypham/Snort-Setup/refs/heads/images/image4.png)

## 🎮 Usage
- Describe how to use the project
- Example command-line usage:
   ```bash
   python script.py --option value
   ```

## 🔍 Intrusion Detection with Snort
Snort is an open-source IDS/IPS that helps monitor and prevent malicious network activity. Below are the steps to install and configure Snort on Ubuntu.

### 📌 Steps to Install & Set Up Snort
#### Step 1: Install Snort
```bash
sudo apt-get install snort -y
```
- Set `HOME_NET` to your network (e.g., `192.168.0.0/24`).
- Verify installation:
```bash
snort --version
```

#### Step 2: Enable Promiscuous Mode
```bash
ip a  # Check network interface
sudo ip link set <your_network_interface> promisc on
```
Replace `<your_network_interface>` with your actual interface name.

#### Step 3: Configure Snort
```bash
sudo cp /etc/snort/snort.conf /etc/snort/snort.conf.backup
sudo nano /etc/snort/snort.conf
```
Set `HOME_NET` to your network range.

#### Step 4: Add Custom Rules
Edit `local.rules` to define custom detections:
```bash
sudo nano /etc/snort/rules/local.rules
```
Example rule to detect pings:
```bash
alert icmp any any -> $HOME_NET any (msg: "ICMP PING DETECTED"; sid:1000001; rev:1;)
```

#### Step 5: Run Snort
```bash
sudo snort -q -l /var/log/snort -i <your_network_interface> -A console -c /etc/snort/snort.conf
```
When Snort detects a ping, it logs and alerts administrators.

## 📸 Screenshots
![Screenshot 1](https://your-image-link.com)
![Screenshot 2](https://your-image-link.com)

## 🔒 Security Considerations
- Regularly update Snort rules.
- Monitor logs for suspicious activity.

## 📜 License
This project is licensed under the [MIT License](LICENSE).

## 👤 Author
- **Your Name** – [GitHub](https://github.com/your-username) | [LinkedIn](https://linkedin.com/in/your-profile)

## 🤝 Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss.

## ⭐ Acknowledgments
- Thanks to contributors and resources that helped with the project.

---
Feel free to modify this `README.md` with relevant information!
