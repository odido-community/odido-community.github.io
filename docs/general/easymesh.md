# What is EasyMesh?

EasyMesh is a Wi-Fi standard developed by the Wi-Fi Alliance that allows routers, access points, and extenders from different manufacturers to work together in a unified mesh Wi-Fi network. Unlike traditional proprietary mesh systems that require you to buy devices from the same brand, EasyMesh ensures interoperability across certified devices.

!!! warning
    While EasyMesh-certified devices are designed to work together, feature support may vary between brands.

## How EasyMesh Works

In an EasyMesh network:

- One device acts as the controller (usually your router).
- Other devices, such as additional Wi-Fi extenders, act as agents.
- These agents automatically connect to the controller and coordinate to provide seamless, stable wireless coverage your home.

The controller dynamically manages:

- **Client Steering**: Automatically directs devices like phones or laptops to the optimal access point based on signal strength and network load.
- **Band Steering**: Moves devices between the 2.4GHz and 5GHz bands for the best balance of speed and coverage.
- **Centralized Configuration**: Syncs network settings — including SSID, passwords, security protocols, and guest network access — across all mesh nodes.

``` mermaid
flowchart TD
    Internet((Internet))

    %% Mesh nodes
    Controller(Main Router - Controller)
    Agent1(Wi-Fi Extender 1 - Agent)
    Agent2(Wi-Fi Extender 2 - Agent)

    %% Main devices
    MainDevice1(Device A - Main)
    MainDevice2(Device B - Main)

    %% Guest devices
    GuestDevice1(Device X - Guest)
    GuestDevice2(Device Y - Guest)

    %% Topology
    Internet --> Controller
    Controller --> Agent1
    Controller --> Agent2

    %% Main network connections
    Controller --> MainDevice1
    Agent1 --> MainDevice2

    %% Guest network connections
    Controller --> GuestDevice1
    Agent2 --> GuestDevice2
```

## What is 802.11v?

802.11v is a Wi-Fi standard that enables wireless network management features to improve how client devices interact with access points. It’s part of a suite of enhancements used in mesh and enterprise-grade networks to deliver a smoother and more efficient Wi-Fi experience.

### How 802.11v Helps with Client and Band Steering

- Client Steering:
    802.11v allows the network to gently guide devices to a better access point when the signal is weak or when another node is less congested. It does this by sending “BSS Transition Management” requests to compatible clients, suggesting a move to a specific AP.
- Band Steering:
    On dual-band networks (2.4GHz and 5GHz), 802.11v helps steer devices to the most appropriate band based on performance, congestion, and signal quality. This helps prevent slowdowns when too many devices crowd the 2.4GHz band.

!!! note 
    For 802.11v to work, the client device (e.g., phone, laptop) must also support it. Most modern smartphones and laptops do.

### The Client Is Still in Control

While 802.11v provides mechanisms for improving Wi-Fi performance — such as client steering and band steering — it’s important to understand that it does not force devices to switch access points or frequency bands.

Instead, 802.11v allows the network (e.g., your router or mesh controller) to send BSS Transition Management Requests. These are essentially suggestions telling a client device:

> “Here’s a better access point you might want to connect to.”

However, the final decision always lies with the client device. It can choose to accept the suggestion or stay connected to its current access point.

This means that:

- Not all devices will roam as expected, even if 802.11v is supported.
- Some older or budget devices may ignore roaming suggestions entirely.
- Roaming behavior can vary significantly between device types and operating systems.

``` mermaid
graph TD
    A1[Client connected to AP1] --> A2[AP1 sends BSS Transition Request]
    A2 --> A3[Client evaluates suggestion]
    A3 -->|Accept| A4[Client disconnects from AP1]
    A4 --> A5[Client connects to AP2 with better signal]
    A3 -->|Reject| A6[Client stays on AP1 with weaker signal]
```