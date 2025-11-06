# Personal-Firewall

This project is designed to monitor, filter, and control network traffic on your system based on user-defined rules.
It acts as a mini firewall, built completely in Python — a simplified version of what real firewalls (like Windows Defender or iptables) do.

# How it Works

# 1. Packet Sniffing (using Scapy)

- The firewall continuously monitors all incoming and outgoing packets on your system.

- It inspects each packet’s:

   Source IP (where it’s coming from)

   Destination IP (where it’s going)

   Port number

   Protocol (TCP, UDP, ICMP, etc.)

# 2. Rule Checking

- You have a file called `rules.json` which contains your firewall rules.

- Each rule defines what traffic to allow or block.

# 3. Logging (Audit Trail)

Every packet — allowed or blocked — is written into firewall.log.

Example log:

`[BLOCKED] TCP packet from 192.168.1.5 to port 22`

`[ALLOWED] ICMP packet from 8.8.8.8 `

# 4. Graphical User Interface (GUI)

- The `gui_firewall.p`y file opens a Tkinter window where you can:

- Start/Stop firewall

-View live logs

-Add or remove rules dynamically

So it’s user-friendly and visual.

   Your Python program watches your network traffic in real-time, checks if it matches any “bad” IP or port, blocks or logs it, and gives you a live monitoring window.

# Commands To Run The Project ( Linux )

- Step 1: Go to your project folder
  
      cd ~/personal_firewall_complete

- Step 2: Install all requirements

      sudo apt update
  
      sudo apt install python3 python3-pip python3-tk -y

      pip install scapy

- step 3: Run the CLI version (main firewall)

      sudo python3 firewall.py

     To stop it, press:

    `Ctrl + C`

- Step 4: Run the GUI version (optional)

  if you want the Tkinter GUI, run

      python3 gui_firewall.py

- Step 5: Check Logs

      cat firewall.log

## Files
- `firewall_core.py` - core engine (rule engine, iptables helper, sniff wrapper)
- `firewall.py` - CLI launcher (`sudo python3 firewall.py`)
- `gui_firewall.py` - Tkinter GUI (start/stop, add/remove rules, live log)
- `rules.json` - sample rules
- `iptables_helper.sh` - helper to flush iptables
- `firewall.log` - runtime log (auto-created)
- `requirements.txt` - dependencies

## Requirements
- Linux (Ubuntu / Kali / WSL)
- Python 3.8+
- scapy (`pip3 install scapy`)
- (optional) python3-tk for GUI: `sudo apt install python3-tk`
