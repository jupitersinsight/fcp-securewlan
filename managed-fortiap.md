# Managed FortiAP

## Overview
FortiAPs directly controlled by a local Fortigate device do not require additional licenses to use UTP services, while standalone or branch FortiAPs managed by FortiLAN Cloud do require licenses for UTP modules.  
The maximum number of supported APs varies based on the Fortigate model.  

**Key benefits of FortiAP managed by FortiGate**:
- Zero-touch deployment
- Single-pane of management
- Security Fabric integration (IPS, application control, web filter...)
- Scalability
- Automation

## FortiAP Adoption
Before FortiAP adoption the administrator must enable the Wireless Controller either from the GUI or from the CLI `config system global/set wireless-controller enable;end`.  
Select the right *WiFi Country/Region* under WiFi Settings from the GUI.  

Once an AP is plugged into the network it starts sending out discovery requests to find an available Controller:  
- Static: the AP is configure with a static controller IP
- DHCP: the AP uses DHCP Option 138 to get the controller IP (4 concatenaed hexadecimal octet of the IP: es. 192.168.0.1 is C0A08001)
- DNS: the AP can discover the controller by using a hostname configured in the AC_HOSTNAME_1 parameter (from AP GUI or CLI)
- FortiLAN Cloud: the AP uses the hostname apctrl1.forticloud.com for FortiLAN Cloud management
- Multicast: discovery requests are sent on multicast address 224.0.1.140 (if multicast routing is configured correctly there i no need for the AP and the Controller to be in the subnet)
- Broadcast: broadcast discovery requests to locate the local controller

By default, discovery requests are sent out every 5 seconds.  

## CAPWAP
**CAPWAP** (Control and Provisioning of Wireless Access Points) is a network protocol that the administrator che use to provision and manage FortiAP devices.  
A **Security Fabric Connection** must be enabled on the interface the FortiGate uses to connect FortiAP devices. DHCP too must be enabled.  
CAPWAP uses UDP port 5246 as the control channel while UDP 5247 as the data channel. Optional DTLS encryption make data communications secure.  

## FortiAP Authorization
By default, manual AP authorization is needed to make an AP active and available.  
This method can be overwritten to let new discovered APs authorized automatically:
```
config system interface
  edit <interface where FortiAP is connected>
    set auto-auth-extension-device enable
end
```

## FortiAP Firmware Update
FortiAP firmware AP can be automatic or manual. From the GUI only one AP per time can be upgraded while from the CLI it is possible to upgrade all FortiAP devices at once.  

## FortiAP Administrator Login
Default credentials *admin/null* must be changed accessing the FortiAP administrative panel.  





   
