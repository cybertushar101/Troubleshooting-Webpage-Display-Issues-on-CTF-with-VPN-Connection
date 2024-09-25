"I spent several weeks trying to fix this VPN connection issue with TryHackMe & HackTheBox. 😔

Scenario:
When you try to access a TryHackMe lab machine's webpage, it freezes and doesn't load. In your browser, you see the status saying “Waiting on 10.10.x.x”.

Solution:
Disconnect from the VPN.

Open your terminal and run this command, replacing <INTERFACE> with your network connection name (e.g. eth0):

bash
Copy code
sudo ip link set dev <INTERFACE> mtu 1200
Reconnect to the VPN by running the following command:

bash
Copy code
sudo openvpn /path-to-file/file.ovpn
This should fix the issue.

If it doesn't, check if tun0 has an MTU of 1200 with this command:

bash
Copy code
sudo ip link show dev tun0
If the MTU isn't 1200, run this command to set it:

bash
Copy code
sudo ip link set dev tun0 mtu 1200
Finally, confirm the MTU value with the ip link show command."
