
# Fix issues with loading lab machine webpages on TryHackMe when connected to the VPN.

"Troubleshooting Webpage Display Issues on TryHackMe with VPN Connection"

## Scenario:


When you try to access a TryHackMe lab machine's webpage, it freezes and doesn't load. In your browser, you see the status saying “Waiting on 10.10.x.x”.


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

![App Screenshot](https://via.placeholder.com/468x300?text=App+Screenshot+Here)

If the MTU isn't 1200, run this command to set it:

```bash
sudo ip link set dev tun0 mtu 1200
```
![App Screenshot](https://via.placeholder.com/468x300?text=App+Screenshot+Here)

Finally, confirm the MTU value with the ip link show command."






