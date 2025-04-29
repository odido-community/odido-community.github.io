# Geust Network

All Odido modems offer the option to enable a Guest Network.
This network allows you to connect guest devices — or any devices you don’t want on your main network — to the internet securely.
Devices connected to the Guest Network cannot access devices on your main network, and devices on your main network cannot access devices on the Guest Network.
This ensures better security and separation between trusted and untrusted devices.

- Guest devices **cannot** talk to each other.
- Guest devices **cannot** talk to the main network.
- Main network devices **cannot** talk to the guest network.
- Both networks **can** access the internet.


``` mermaid
flowchart TD
    Internet((Internet))
    MainNetwork(Main Network)
    GuestNetwork(Guest Network)

    MainDevice1(Device A - Main)
    MainDevice2(Device B - Main)

    GuestDevice1(Device X - Guest)
    GuestDevice2(Device Y - Guest)

    Internet --> MainNetwork
    Internet --> GuestNetwork

    MainNetwork --> MainDevice1
    MainNetwork --> MainDevice2

    GuestNetwork --> GuestDevice1
    GuestNetwork --> GuestDevice2

    %% Blocked communications
    MainNetwork -.X.-> GuestNetwork
    GuestNetwork -.X.-> MainNetwork

    GuestDevice1 -.X.-> GuestDevice2
    GuestDevice2 -.X.-> GuestDevice1
```

## Configure

You can Enable the Geust network with the steps below;

1. Log in to the Web UI.
2. On the main dashboard, locate the tile labeled **Guest Network**.
3. In the Guest Network settings, toggle the 2.4GHz and/or 5GHz guest networks on.
    Depending on your preference. You can enable either or both bands.

## Mesh

When you enable the Guest Network, it will automatically be activated on all access points that are part of your mesh network.
This ensures that guest devices can connect to the Guest Network seamlessly throughout your entire home, no matter which access point they are near.

!!! note
    Guest devices will remain isolated from your main network and from each other, even when connected through different access points.
