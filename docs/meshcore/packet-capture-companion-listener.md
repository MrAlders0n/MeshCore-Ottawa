# MeshCore Packet Capture (Companion Node Listener)
**Purpose:**  
This guide explains how to install and run [MeshCore Packet Capture](https://github.com/agessaman/meshcore-packet-capture) on a **Debian-based system** (such as Raspberry Pi OS or Ubuntu) to stream captured packets from a **dedicated MeshCore companion node** to the [MeshCore Packet Analyzer](https://analyzer.letsme.sh/o).

**Scope:**  
This setup covers **packet capture from companion nodes only**.  
Packet capture for **repeaters** and **room servers** is supported by MeshCore but not yet documented on this page.

## Requirements
* A **Debian-based operating system** (Raspberry Pi OS, Ubuntu, or equivalent)  
* A **dedicated MeshCore companion node** connected via USB or TCP bridge  
* **Internet access** for sending packet data to analyzer servers  

## 1. Companion Configuration
Before installing, ensure your companion node is properly configured and named according to the Ottawa MeshCore naming standard.

Each companion should follow the format:

<pre>
YOW_<LOCATION>
</pre>

For example:
* `YOW_Barrhaven`
* `YOW_Centretown`
* `YOW_Orleans`

This helps the MeshCore Packet Analyzer identify which area each listener belongs to and keeps the Ottawa network consistent.

## 2. Install Dependencies
Run the following commands to update your system and install required packages:

<pre>
sudo apt update
sudo apt install -y python3 curl git
sudo apt install -y python3.12-venv
</pre>

## 3. Install the MeshCore Decoder (Required for Auth)
**meshcore-decoder** is required for authentication when publishing packets to the MeshCore Packet Analyzer.

<pre>
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
source ~/.bashrc
nvm install --lts
npm install -g @michaelhart/meshcore-decoder
</pre>

Verify installation:

<pre>
which meshcore-decoder
</pre>

Once installed, proceed with running the MeshCore Packet Capture installer.

## 4. Run the Packet Capture Installer
Run the official installation script:

<pre>
bash <(curl -fsSL https://raw.githubusercontent.com/agessaman/meshcore-packet-capture/main/install.sh)
</pre>

In this example, a **TCP connection** was used.  
When prompted, you will be asked how you want to connect to your MeshCore device.  
Choose the option that matches your setup:

;1) Bluetooth Low Energy (BLE)
: • Recommended for T1000 devices  
: • Wireless connection  
: • Works with MeshCore T1000e and compatible devices  

;2) Serial Connection
: • For devices with USB or serial interface  
: • Uses a direct USB/serial cable connection  
: • Most reliable for continuous operation  

;3) TCP Connection
: • For network-connected devices  
: • Connects to your node over the network  
: • Works with ser2net or other TCP-to-serial bridges  

The installer is interactive and runs through several stages with clear headers.  
Below is an example of a successful run and what you should expect to see.

<pre>
═══════════════════════════════════════════════════
  MeshCore Packet Capture Installer v1.1.1
═══════════════════════════════════════════════════

This installer will help you set up MeshCore Packet Capture.

Installation directory [/home/user/.meshcore-packet-capture]:
ℹ Installation directory: /home/user/.meshcore-packet-capture

═══════════════════════════════════════════════════
  Installing Files
═══════════════════════════════════════════════════
ℹ Downloading from GitHub (agessaman/meshcore-packet-capture @ main)...
✓ Files downloaded and verified

═══════════════════════════════════════════════════
  Checking Dependencies
═══════════════════════════════════════════════════
✓ Python 3 found: Python 3.12.3
✓ Virtual environment created
✓ Python dependencies installed
✓ meshcore-decoder found: /home/user/.nvm/versions/node/v24.11.0/bin/meshcore-decoder

═══════════════════════════════════════════════════
  Device Connection Configuration
═══════════════════════════════════════════════════
Select connection type [1-3] [1]: 3
ℹ Selected: TCP Connection
TCP host/address [localhost]: 192.168.1.201
TCP port [5000]:
✓ TCP connection configured: 192.168.1.201:5000

Enter your IATA code (3 letters): YOW
✓ IATA code set to: YOW

═══════════════════════════════════════════════════
  MQTT Broker Configuration
═══════════════════════════════════════════════════
Enable the MeshCore Packet Analyzer (US + EU servers) for redundancy? [Y/n]: Y
✓ MeshCore Packet Analyzer brokers enabled

═══════════════════════════════════════════════════
  Installation Method
═══════════════════════════════════════════════════
Choose installation method [1-3] [1]: 1
ℹ Installing systemd service...
✓ Service enabled
✓ Systemd service installed

═══════════════════════════════════════════════════
  Installation Complete!
═══════════════════════════════════════════════════
Installation directory: /home/user/.meshcore-packet-capture
Configuration file: /home/user/.meshcore-packet-capture/.env.local
✓ Installation complete!
</pre>

If you see:
<pre>
✗ Service failed to start
</pre>

it usually means the node wasn’t reachable during setup.  
Check your TCP or Serial connection and restart the service manually:

<pre>
sudo systemctl restart meshcore-capture
</pre>

## 5. Managing the System Service
The installer creates a *systemd* service named **meshcore-capture**.

<pre>
sudo systemctl start meshcore-capture
sudo systemctl stop meshcore-capture
sudo systemctl status meshcore-capture
sudo journalctl -u meshcore-capture -f
</pre>

If it fails to start, confirm:
* The companion node is powered and reachable  
* The TCP or Serial settings in  
  <code>/home/&lt;user&gt;/.meshcore-packet-capture/.env.local</code> are correct

## 6. Verifying Connection
Once running, you should see packets appear in the MeshCore Packet Analyzer dashboard:

**[https://analyzer.letsme.sh/status/observers](https://analyzer.letsme.sh/status/observers)**

Open the link above and use the **All Regions** dropdown in the top right to select your IATA region (e.g., **YOW**).  
This will filter the view to show packet activity from your region and confirm your listener is forwarding data correctly.

## 7. Logs and Troubleshooting
To view live logs:

<pre>
sudo journalctl -u meshcore-capture -f
</pre>

### Common Issues
* **Connection refused:** Check TCP host/port  
* **meshcore-decoder not found:** Re-run Step 2  
* **No packets visible:** Ensure the node is on the correct channel/frequency  

## 8. Next Steps
Future documentation will include:
* Packet capture for **repeaters**  
* Packet capture for **room servers**  

## 9. Example Configuration
A sample configuration file (``.env.local``) may look like this:

<pre>
# MeshCore Packet Capture Configuration
# This file contains your local overrides to the defaults in .env

# Update source (configured by installer)
PACKETCAPTURE_UPDATE_REPO=agessaman/meshcore-packet-capture
PACKETCAPTURE_UPDATE_BRANCH=main

# Connection Configuration
PACKETCAPTURE_CONNECTION_TYPE=tcp

# Companion Adverts
PACKETCAPTURE_ADVERT_INTERVAL_HOURS=24
PACKETCAPTURE_TCP_HOST=192.168.1.201
PACKETCAPTURE_TCP_PORT=5000

# Location Code
PACKETCAPTURE_IATA=YOW

# Advert Settings
PACKETCAPTURE_ADVERT_INTERVAL_HOURS=11

# Logging Settings
PACKETCAPTURE_LOG_LEVEL=INFO

# MQTT Broker 1 - MeshCore Packet Analyzer (US)
PACKETCAPTURE_MQTT1_ENABLED=true
PACKETCAPTURE_MQTT1_SERVER=mqtt-us-v1.letsmesh.net
PACKETCAPTURE_MQTT1_PORT=443
PACKETCAPTURE_MQTT1_TRANSPORT=websockets
PACKETCAPTURE_MQTT1_USE_TLS=true
PACKETCAPTURE_MQTT1_USE_AUTH_TOKEN=true
PACKETCAPTURE_MQTT1_TOKEN_AUDIENCE=mqtt-us-v1.letsmesh.net
PACKETCAPTURE_MQTT1_KEEPALIVE=120

# MQTT Broker 2 - MeshCore Packet Analyzer (EU)
PACKETCAPTURE_MQTT2_ENABLED=true
PACKETCAPTURE_MQTT2_SERVER=mqtt-eu-v1.letsmesh.net
PACKETCAPTURE_MQTT2_PORT=443
PACKETCAPTURE_MQTT2_TRANSPORT=websockets
PACKETCAPTURE_MQTT2_USE_TLS=true
PACKETCAPTURE_MQTT2_USE_AUTH_TOKEN=true
PACKETCAPTURE_MQTT2_TOKEN_AUDIENCE=mqtt-eu-v1.letsmesh.net
PACKETCAPTURE_MQTT2_KEEPALIVE=120

# MQTT Topics for Broker 1 - Default Pattern
PACKETCAPTURE_MQTT1_TOPIC_STATUS=meshcore/{IATA}/{PUBLIC_KEY}/status
PACKETCAPTURE_MQTT1_TOPIC_PACKETS=meshcore/{IATA}/{PUBLIC_KEY}/packets
</pre>
