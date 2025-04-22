# Mikrotik

Setting up a MikroTik router with an Odido internet connection boosts performance, security, and management. MikroTik routers are powerful and affordable. In this post, we’ll walk you through the steps to get your MikroTik router running with Odido.

!!! info
    For this guide we used **Mikrorik CCR2004-16G-2S+** running **RouterOS 7.16.2**

## Connect to the router

To configure the MikroTik router, you’ll first need to establish a connection. We recommend using either a serial cable or an SSH connection. These methods allow you to easily copy and paste the configuration commands provided below, making the setup process more efficient and error-free.

### Using a Serial Cable

1. Connect the serial cable to the MikroTik router and your computer.
2. Use terminal software like PuTTY (Windows), screen (Linux), or Serial (macOS).
3. Configure the terminal software with the following settings:
  - **Baud Rate** : 115200
  - **Data Bits** : 8
  - **Stop Bits** : 1
  - **Parity** : None
  - **Flow Control** : None
4. Open the connection, and you’ll see the MikroTik console.
5. When prompted, enter the default username `admin` and leave the password field blank (default).

### Using SSH
1. Connect your computer to one of the LAN ports of the MikroTik router using an Ethernet cable.
2. Ensure your computer is set to obtain an IP address automatically (DHCP). The router will assign your computer an IP address.
3. Find the default IP address of the MikroTik router (usually 192.168.88.1) and use SSH to connect.
4. When prompted, enter the default username `admin` and leave the password field blank (default).

First, we’ll configure the LAN ports to establish a network connection for all your devices. This will ensure that both your homelab and internet access are set up properly, providing seamless connectivity throughout your network.

## LAN

### Bridge Interface

we’ll create a bridge interface, allowing us to combine all the ports into a single network. This will enable seamless communication between all your devices on the same network.

!!! warning
    Make sure to adjust the information below to your model and setup.

```bash
/interface bridge
add name=bridge1 protocol-mode=none
/interface bridge port
add bridge=bridge1 interface=ether2
add bridge=bridge1 interface=ether3
add bridge=bridge1 interface=ether4
add bridge=bridge1 interface=ether5
add bridge=bridge1 interface=ether6
add bridge=bridge1 interface=ether7
add bridge=bridge1 interface=ether8
/interface list
add name=LAN
/interface list member
add interface=bridge1 list=LAN
/ip address
add address=192.168.1.1/24 interface=bridge1 network=192.168.1.0
```

### DHCP

Now, we’ll set up a DHCP server to automatically assign IP addresses to all the devices connected to your network.

```bash
/ip dhcp-server network
add address=192.168.1.0/24 dns-server=192.168.1.1 gateway=192.168.1.1 netmask=24
/ip pool
add name=dhcp_pool0 ranges=192.168.1.100-192.168.1.254
/ip dhcp-server
add address-pool=dhcp_pool0 interface=bridge1 lease-time=1d name=dhcp1
```

### DNS

Next, we’ll enable DNS queries on the router and configure it to forward those queries to the upstream DNS server. This will ensure that your devices can resolve domain names and access websites without any issues.

```bash
/ip dns
set allow-remote-requests=yes
```

## Firewall

The firewall will be configured to block all incoming traffic by default, only allowing connections that are established, related, or untracked. Outgoing traffic will be permitted solely from the LAN side, ensuring secure and controlled communication between your devices and the internet.

```bash
/ip firewall filter
add action=accept chain=forward comment="Allow established,related,untracked" connection-state=established,related,untracked
add action=drop chain=forward comment="drop invalid traffic" connection-state=invalid
add action=accept chain=forward comment="port forwarding" connection-nat-state=dstnat
add action=accept chain=forward comment="internet traffic" in-interface-list=LAN out-interface-list=WAN
add action=drop chain=forward comment="drop all else"
add action=accept chain=input comment="Allow established,related,untracked" connection-state=established,related,untracked
add action=drop chain=input comment="Drop invalid" connection-state=invalid
add action=accept chain=input comment="Allow traffic from LAN interface list to the router" in-interface-list=LAN
add action=drop chain=input comment="Drop all else"
/ip firewall service-port
set ftp disabled=yes
set tftp disabled=yes
set h323 disabled=yes
set sip disabled=yes
```

## WAN

We’ll need to configure the WAN interface to obtain an IP address from your ISP. In this setup, the physical interface `ether1` will be used to connect to your ISP. Make sure to replace all the placeholders between `<>` with the correct information provided by your ISP.

!!! warning
    Make sure to adjust the information below to your model and setup.

```bash
/interface vlan add interface=ether1 name=internet vlan-id=300 
/ip dhcp-client add interface=internet disabled=no use-peer-ntp=no add-default-route=yes 
/interface list add name=WAN 
/interface list member add interface=internet list=WAN
```

## NAT

We’ll now set up a NAT rule to translate all outgoing traffic from your local network to your public IP address. This will enable devices in your homelab to access the internet using the router’s public IP, ensuring proper routing and security for all outgoing connections.

```bash
/ip firewall nat
add action=masquerade chain=srcnat comment="Enable NAT on WAN interface" out-interface-list=WAN
```

## System

We’ll create a new user account with the necessary privileges and then disable the default user account. This will help prevent unauthorized access and ensure that only trusted users can manage the router. As well we you can change the hostname for the router.

### User Account

```bash
/user add name=<Username> password=<Password> group=full
/user disable admin
```

> * Replace `<Username>` to your new username
> * Replace `<Password>` to your new password

### Hostname

```bash
/system identity
set name=<Your hostname>
```

### NTP

To ensure the router displays the accurate time, we’ll configure the correct timezone.

```bash
/system ntp client
set enabled=yes
/system ntp client servers
add address=time.cloudflare.com
/system clock
set time-zone-name=Europe/Amsterdam
```

Now your MikroTik router is fully configured for Odido Internet! 🎉 With a secure and efficient network in place, you’re all set for smooth browsing, streaming, and more. Happy networking! 🤝