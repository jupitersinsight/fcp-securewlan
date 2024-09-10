# Wireless Security

## Types of SSID

- Tunnel mode: traffic is tunneled back to wireless controller using CAPWAP data channel, meaning that all traffic goes through firewall policies and threat scanning before being put on the esgress interface
Tunneled SSIDs are treated as Layer 3 interfaces, therefore, administrators can configure DHCP and DNS parameters.
- Bridge mode: traffic is bridged directly to the local LAN that AP is connected to, meaning that traffic is placed in the VLAN and passed over (some APs can perform threat scanning before putting data onto the wired connection).
Traffic is subject to firewall policies applied to the VLAN. Only specific FortiAP models support security profiles (Antivirus, IPS, Web filtering, Application control). Requires a separate Fortiguard subscription per AP.
- Wireless mesh: used as backhaul SSID in a distributed connection

## Wireless Ecnryption
802.1X is a standard designed to provide authentication services to network devices that want to join a local wired or wireless network.  
Clients (called *supplicants*) are allowed access to the Layer2 until their credentials are passed from the *authenticator* (a switch or an access point) to the *authentication server* (such as FortiAuthenticatitor or a server running RADIUS and EAP).  
If the authentication is successful the client is allowed access to the network.  


