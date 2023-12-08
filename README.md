# CSN-150-Final-Project

1- After acquiring a GL iNet travel router and with the release of RouterOS 7 by Mikrotik, I decided to set up a continuous VPN connection using Mullvad on my Mikrotik CHR. In this post, I'll detail the process of configuring Mikrotik CHR to use Mullvad VPN with WireGuard, implementing a kill switch, and utilizing Mullvad DNS.

2- Interface Configuration: Create a WireGuard interface named "Mullvad" in the RouterOS terminal.Use the WireGuard-config generator to either upload the private key or let Mullvad generate one for you. Select a country, city, and server and download the configuration file.

3- WireGuard Peer Setup:If uploading your key, copy the private key from the terminal output and import it into the WireGuard-config generator. If Mullvad generates the key, copy the PrivateKey value from the config file and set it in the RouterOS terminal. Add a WireGuard peer using the server details obtained from the config file.

4- IP and Routing: Set up IPv4 and IPv6 addresses using information from the [Interface] section of the config file. Create a routing table, add a default route, and ensure the parameters match your server's details.

5- Firewall Rules: Set up masquerade and firewall rules for both IPv4 and IPv6 to mark and route traffic through the Mullvad interface. Add rules to drop incoming traffic for

5- DNS Configuration: Disable DoH or DoT in your browser to avoid DNS leaks. Choose a Mullvad DNS server with specific features and set it in the Mikrotik config. Create a mangle rule to route DNS requests through the VPN.

6- Port Forwarding (Optional): Generate a random port from Mullvad's portal for incoming connections. Create a netmap rule for port forwarding to an internal server.
