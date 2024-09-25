
# Fix issues with loading lab machine webpages on TryHackMe when connected to the VPN.


Extended Description for GitHub Repo: Troubleshooting Webpage Display Issues on TryHackMe with VPN Connection
Overview
This repository provides solutions to a common issue faced by users when accessing TryHackMe lab machines while connected to a VPN. The problem typically occurs when a webpage hosted on a TryHackMe lab machine fails to load, leaving the browser stuck on "Waiting on 10.10.x.x" and freezing. This can be a frustrating issue, especially when trying to complete labs and challenges on TryHackMe.

## Scenario: 


When you try to access a TryHackMe & HackTheBox lab machine's webpage, it freezes and doesn't load. In your browser, you see the status saying “Waiting on 10.10.x.x”.


![Screenshot 2024-09-26 001701](https://github.com/user-attachments/assets/076c9e39-3a5b-417e-8cdb-e9b0ba8603bd)


## Step-by-Step Solution:
1. Disconnect from the VPN
First, ensure that you disconnect from the TryHackMe VPN before proceeding with any changes.

2. Adjust the MTU on Your Local Network Interface
Run the following command in your terminal to set the MTU of your network interface (replace <INTERFACE> with the name of your interface, such as eth0):

## commands

```bash
sudo ip link set dev <INTERFACE> mtu 1200
```

This adjustment reduces the packet size to prevent fragmentation, which can cause network slowdowns and webpage loading issues when connected to the VPN.

3. Reconnect to the VPN
After adjusting the MTU, reconnect to the TryHackMe VPN using OpenVPN:

```bash
sudo openvpn /path-to-file/file.ovpn
```

This will restore your VPN connection with the new MTU setting applied.

4. Verify and Adjust the VPN MTU
If the problem persists, verify that the MTU for the VPN's virtual interface (tun0) is set correctly:


## Screenshots

```bash
sudo ip link show dev tun0
````

![Screenshot 2024-09-25 231905](https://github.com/user-attachments/assets/3c595556-53b9-4db7-8dd4-130cb86b73b2)

If the MTU is not set to 1200, manually adjust it:

```bash
sudo ip link set dev tun0 mtu 1200
```
![Screenshot 2024-09-25 232350](https://github.com/user-attachments/assets/18ca12d9-ffd7-4422-b990-27ce7c69730c)

Finally, confirm the MTU setting using the ip link show command to ensure it has been applied properly.


## Now You can check Your MTU Value is changed or not from following command
```bash
sudo ip link show dev tun0
```

![Screenshot 2024-09-25 232402](https://github.com/user-attachments/assets/715d952d-bdd9-4bd8-9f69-6a528de412a3)





