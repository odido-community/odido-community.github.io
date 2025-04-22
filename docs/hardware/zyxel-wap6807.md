# Zyxel WAP6807
The **Zyxel WAP6807** is a high-performance WiFi 6 mesh extender designed to expand and enhance wireless coverage in homes and small offices. Built for seamless integration with EasyMesh-compatible routers, it ensures consistent performance across your network and eliminates dead zones, even in challenging environments.

## Deployment
This model is typically supplied as a WiFi extender using EasyMesh-compatible gateways, such as the [**Zyxel T50**](./zyxel-vmg8825.md).

## Key Features
- **WiFi 5 (802.11ac)** for faster speeds and higher efficiency  
- **Dual-band operation** on 2.4GHz and 5GHz  
- **EasyMesh support** for seamless roaming and centralized management  
- **4x4 MU-MIMO** antennas for better performance with multiple devices  
- **Compact design** for flexible placement  
- **Secure wireless encryption** with WPA/WPA2
- **LED indicators** for signal strength and system status

## Specifications

### Wireless
- **2.4GHz Band**: Up to 300 Mbps[^1]  
- **5GHz Band**: Up to 1733 Mbps[^1]  
- **WPA/WPA2 security** for modern encryption  
- **Automatic channel selection** for optimal performance

### Ethernet
- 2x Gigabit RJ45 LAN port  
    - Can be used to wirelessly bridge to nearby wired-only devices

### Mesh Capabilities
- **EasyMesh** support for automatic syncing with [compatible routers](#deployment) 
- **Seamless roaming** between main router and extender  
- **Single SSID** operation for entire home network  

## Configuration Options
The Zyxel WAP6807 is configured automatically via the main router. There are no configuration settings to be changed on the devices directly.

## Admin Access
- Default access via browser at the assigned IP (e.g., `192.168.1.x`)  
- Default login credentials are printed on the device label  
- It is highly recommended to change the default password during setup for security reasons   

## Firmware Updates
Odido may periodically push firmware updates to improve stability and security.

[^1]: These are theoretical maximum speeds. Actual throughput depends on network conditions, signal strength, and client capabilities.
