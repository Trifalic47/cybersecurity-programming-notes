---
aliases:
---

---

# 📡 Airbase-ng: The "No-Router" Rogue AP

**Target Interface:** `wlan0`

**Environment:** Arch Linux

**Goal:** Connect phone to laptop without an external router to monitor logs.

## ⚡ Phase 1: Clean the Environment

Before starting, you must stop processes that will try to "steal" `wlan0` back from you.

```
# Kill background managers
sudo airmon-ng check kill

# Start Monitor Mode
sudo airmon-ng start wlan0
```

_Note: Your interface is now likely named `wlan0mon`._

## 🚀 Phase 2: The 3-Terminal Execution

Open three separate terminal tabs. Follow these in order.

### Tab 1: The Radio Signal

This starts the broadcast. Keep this running.

```
sudo airbase-ng -e "Tanishq_Lab" -c 6 wlan0mon
```

> [!NOTE]
> 
> Once this starts, airbase-ng creates a new virtual interface called `at0`.

### Tab 2: The Interface Logic

We must give `at0` an IP address so it acts like a Gateway.

```

sudo ip link set at0 up
sudo ip addr add 10.0.0.1/24 dev at0
sudo ip link set dev at0 mtu 1400
```

### Tab 3: The DHCP Server (The "Brain")

Your phone won't connect unless it gets an IP address. `dnsmasq` acts as the router's brain.

```
# Install if needed: sudo pacman -S dnsmasq
sudo dnsmasq -i at0 --dhcp-range=10.0.0.10,10.0.0.100,12h -d
```

> [!SUCCESS] Watch Terminal 3
> 
> When you try to connect your phone, you should see `DHCPDISCOVER` and `DHCPOFFER` appearing here.

## 🕵️ Phase 3: Monitoring the Phone Logs

Once the phone shows "Connected" (it will say "No Internet", which is fine), open a **4th terminal** to sniff the traffic.

### Option A: Standard Tshark (Text-based)

```
sudo tshark -i at0
```

### Option B: HTTP URL Sniffing

```
# Shows every website/server the phone apps are trying to reach
sudo tshark -i at0 -Y http.request -T fields -e http.host -e http.request.uri
```

## 🛠 Troubleshooting the "Saved" Loop

If your phone says **"Saved"** but won't connect:

1. **Firewall:** Arch often has `iptables` rules. Clear them:
    
    `sudo iptables -F`
    
2. **NetworkManager:** Sometimes it's still alive. Disable it for the specific card:
    
    `sudo nmcli device set wlan0mon managed no`
    
3. **Phone settings:** If your phone says "No internet, disconnect?", you **must** select "Stay Connected."
    

**Tags:** #arch-linux #aircrack-ng #rogue-ap #pentesting