# Zyxel T54 (DX5401-B0/B1)

The **Zyxel T54 (DX5401-B0/B1)** is a high-performance dual-band WiFi 6 router engineered to deliver fast, stable, and versatile internet connectivity. Designed with modern homes and small offices in mind, it supports multiple technologies to ensure compatibility with various broadband infrastructures, including xDSL and fiber.

!!! info "Deployment"
    This model is the **default router for xDSL customers**, though it has also been supplied to fiber customers in the past.

## Key Features

- **WiFi 6 (802.11ax)** for enhanced wireless performance and efficiency  
- **Dual-band support**: 2.4GHz and 5GHz for better load distribution  
- **Multiple connectivity options**: xDSL, Ethernet WAN, and USB  
- **VoIP support** with two FXS ports for phone service  
- **Flexible configuration** through a user-friendly web interface  
- **Parental controls** and guest network support for better network management

## Specifications

### Wireless
- 4x4 MU-MIMO antennas for simultaneous device connections  
- **2.4GHz Band**: Up to 1148 Mbps[^1]  
- **5GHz Band**: Up to 4804 Mbps[^1]  
- **OFDMA (Orthogonal Frequency Division Multiple Access)** improves latency and efficiency  
- **EasyMesh** support for seamless WiFi coverage with compatible extenders  
- **Security**: WPA2 and WPA3 for modern encryption standards  

### Ethernet
- 4x Gigabit RJ45 LAN ports for wired devices  
- 1x Gigabit RJ45 WAN port for fiber ONT  

### xDSL
- 1x RJ11 port supporting ADSL, VDSL, and VDSL2 with vectoring  

### Voice (VoIP)
- 2x FXS RJ11 ports for analog telephones  
- Supports SIP accounts for VoIP calling  
- DTMF settings available for caller ID and tone dialing  

### USB
- 1x USB 3.0 port for media sharing, printer sharing, or network storage (NAS)  
- Can be used for SMB or DLNA services  

## Configuration Options
The Zyxel T54 offers a wide range of options to customize and optimize your network environment:

- **Wireless Settings**  
    - Change SSID (WiFi name) and password  
    - Enable or disable wireless radios  
    - Separate SSIDs for each frequency band  

- **LAN/DHCP Configuration**  
    - Define IP ranges  
    - Set static IPs for devices  

- **Port Forwarding**  
    - Allow access to internal services like game servers, cameras, etc.  

- **DMZ Host Setup**  
    - Designate a device to bypass firewall filtering for specific use-cases  

- **Guest Network**  
    - Isolated WiFi for visitors, keeping your main network secure  

- **Dynamic DNS (DDNS)**  
    - Access your network remotely using a hostname instead of an IP  

- **SMB File Sharing**  
    - Access USB-attached storage as a network drive  

- **DLNA Media Server**
    - Stream media to compatible devices like Smart TVs and consoles  

- **Parental Controls**  
    - Restrict access by time  

- **Voice Settings (DTMF)**  
    - Configure tone signaling for better VoIP compatibility  
    - Enable/disable caller ID features  

## Admin Access
- Access the router admin panel via browser: `https://192.168.1.1`  
- Default login credentials are printed on the device label  
- It is highly recommended to change the default password during setup for security reasons  

## Firmware Updates
Odido  periodically releases firmware updates to improve performance and fix security vulnerabilities.  

[^1]: These speeds are theoretical maximums. Actual speeds may vary depending on network conditions and client device capabilities.