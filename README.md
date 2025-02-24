# Snort-Setup

  <img src="https://raw.githubusercontent.com/itstonypham/Snort-Setup/refs/heads/images/download.png" alt="Description" width="35%">

## 📌 Overview
Comprehensive Guide to Snort Intrusion Detection and Prevention Setup.  
<br>

## 🐷 Why Use Snort?
Snort is a popular, open-source Intrusion Detection and Prevention System (IDS/IPS) that monitors network traffic to spot and stop suspicious activity, keeping systems safe. This guide will help you set up and run Snort on Ubuntu.  
<br>

## ✨ How This Helps
- **Real-Time Monitoring**  
Snort watches network traffic and alerts to any suspicious activity.

- **Customizable Alerts**  
Rules can be tailored to detect specific threats relevant to the network.

- **Community Rules**  
Regular updates help stay protected against new threats.  
<br>

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
  ![Description](https://raw.githubusercontent.com/itstonypham/Snort-Setup/refs/heads/images/image1.png)

  ### Step 2: Enable Promiscuous Mode
- Check your network interface:

   ```bash
   ip a
   ```
- Enable Snort to see all network traffic:
    ```bash
   sudo ip link set <your_network_interface> promisc on
   ```
- Replace <your_network_interface> with your network interface name.
  ![Description](https://raw.githubusercontent.com/itstonypham/Snort-Setup/refs/heads/images/image8.png)
  ![Description](https://raw.githubusercontent.com/itstonypham/Snort-Setup/refs/heads/images/image3.png)
  
  ### Step 3: Configure Snort
- Snort files are in /etc/snort. Make a backup:

   ```bash
   sudo cp /etc/snort/snort.conf /etc/snort/snort.conf.backup
   ```
- Edit snort.conf to set HOME_NET to your network range:
    ```bash
   sudo nano /etc/snort/snort.conf
    ```
  ![Description](https://raw.githubusercontent.com/itstonypham/Snort-Setup/refs/heads/images/image9.png)
  ![Description](https://raw.githubusercontent.com/itstonypham/Snort-Setup/refs/heads/images/image13.png)

  ### Step 4: Add Custom Rules
- Open local.rules to add custom rules:

   ```bash
   sudo nano /etc/snort/rules/local.rules
   ```
- For example, add a rule to detect pings:  
alert icmp any any -> $HOME_NET any (msg: "ICMP PING DETECTED"; sid:1000001; rev:1;)

  ![Description](https://raw.githubusercontent.com/itstonypham/Snort-Setup/refs/heads/images/image6.png)
  ![Description](https://raw.githubusercontent.com/itstonypham/Snort-Setup/refs/heads/images/image11.png)
  ![Description](https://raw.githubusercontent.com/itstonypham/Snort-Setup/refs/heads/images/image5.png)

  ### Step 5: Run Snort
- Start Snort to see alerts in real-time:

   ```bash
   sudo snort -q -l /var/log/snort -i <your_network_interface> -A console -c /etc/snort/snort.conf
   ```
- Replace <your_network_interface> with your network interface name.
- When Snort spots a ping request, it triggers an alert saying "ICMP PING DETECTED" and logs details about it. This helps keep an eye on any unusual activity on the network.

  ![Description](https://raw.githubusercontent.com/itstonypham/Snort-Setup/refs/heads/images/image7.png)
  ![Description](https://raw.githubusercontent.com/itstonypham/Snort-Setup/refs/heads/images/image2.png)  
<br>

## 🔚 Conclusion
- Now that Snort is set up, it can spot and get alerts on any suspicious network activity. Keeping an eye on it and updating regularly will help keep the network safe.

## 👤 Author
- **Tony Pham** – [GitHub](https://github.com/itstonypham) | [LinkedIn](https://www.linkedin.com/in/itstonypham/)

## 🤝 Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss.  


## ⭐ Acknowledgments
- Thanks to contributors and resources that helped with the project.

---
