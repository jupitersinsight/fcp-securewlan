# Wireless Network Access

## Block intra-SSID traffic
In tunneled mode SSID, all traffic between wireless clients is blocked.  
In bridge mode SSID, all traffic among clients connected to the same SSID from the same AP is blocked while traffic among clients connected to the same SSID bu different APs is allowed.  

## VLANs
VLANs are tied to tunneled SSID interface like sub-interfaces which need an IP Address configred and requires separate firewall policies.  
Local Bridge with VLANS relies on already existing firewall VLANs and policies.
