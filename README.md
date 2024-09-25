
# Fix issues with loading lab machine webpages on TryHackMe when connected to the VPN.

"Troubleshooting Webpage Display Issues on TryHackMe with VPN Connection"

## Scenario:


When you try to access a TryHackMe & HackTheBox lab machine's webpage, it freezes and doesn't load. In your browser, you see the status saying “Waiting on 10.10.x.x”.


## Solution:
1.Disconnect from the VPN.

2.Open your terminal and run this command, replacing <INTERFACE> with your network connection name (e.g. eth0):

## commands

```bash
sudo ip link set dev <INTERFACE> mtu 1200
```

3.Reconnect to the VPN by running the following command:
```bash
sudo openvpn /path-to-file/file.ovpn
```

This should fix the issue.


However, if it is not resolved, run the following command to ensure tun0 has an MTU of 1200.


## Screenshots

```bash
sudo ip link show dev tun0
````

![Screenshot 2024-09-25 231905](https://github.com/user-attachments/assets/3c595556-53b9-4db7-8dd4-130cb86b73b2)

If the MTU isn't 1200, run this command to set it:

```bash
sudo ip link set dev tun0 mtu 1200
```
![Screenshot 2024-09-25 232350](https://github.com/user-attachments/assets/18ca12d9-ffd7-4422-b990-27ce7c69730c)

Finally, confirm the MTU value with the ip link show command."

## Now You can check Your MTU Value is changed or not from following command
```bash
sudo ip link show dev tun0
```

![Screenshot 2024-09-25 232402](https://github.com/user-attachments/assets/715d952d-bdd9-4bd8-9f69-6a528de412a3)





