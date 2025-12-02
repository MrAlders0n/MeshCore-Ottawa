
# Welcome to Greater Ottawa Mesh Enthusiasts!
* [Join us on Discord!](https://discord.gg/WSyNd8SfNr)

## About
Welcome to the Ottawa mesh group!
See the info below for default frequencies, and please join our Discord to chat with us.

Both **MeshCore** and **Meshtastic** are protocols that run on top of LoRa radios.
LoRa (Long Range) is a low-power modulation suited to long-distance links at modest data rates.
By building on LoRa, both systems enable decentralized, low-cost community networks.

Most of the city is currently running **MeshCore** with some **Meshtastic** presence scattered around.
We have roughly **50 static MeshCore repeaters** around the region, linking Carleton Place, Ashton, Stittsville,
Kemptville, Kanata, Barrhaven, Westboro, Downtown, Old Ottawa South, Vanier, Orléans, and areas near Cumberland.

If you’re interested in playing an active role in the community, we’re always looking for volunteers.
Reach out to **MrAlders0n** with what you’d like to help with.

**Community Outreach**
*Spread the word on social media (e.g., Reddit, Facebook, TikTok), put posters up around the community
**Community Support**
*Welcoming new users in the discord and answering any questions they have
**Fabrication Team**
*For people who want to be involved in custom PCB design
**Knowledge Curators**
*Maintain wiki content
**Tower Tech**
* People who like to climb stuff, help install/maintain repeaters

## MeshCore vs Meshtastic
**Meshtastic** is a peer-to-peer mesh where every node can forward traffic, making it flexible for ad-hoc use but prone to congestion in larger networks.  
Because it relies on nodes that are typically moving, coverage can also be unreliable and sporadic.  

**MeshCore** relies on fixed repeaters for routing, providing a more stable and scalable backbone for city-wide coverage.  

[Watch an overview on YouTube](https://www.youtube.com/watch?v=tXoAhebQc0c)

## MeshCore
To get started and connect to the mesh, begin with a **companion node**.  
Pick a build that fits your needs, then flash MeshCore companion firmware to the device.  

From there, you can explore repeaters builds and mounting options to expand coverage and strengthen the Ottawa mesh.  

### Getting Started
* [Roles Explained](meshcore/hardware-overview.md)
* [F.A.Q](meshcore/meshcore-faq.md)

### Hardware
* [Companion Nodes](meshcore/companion-nodes-antenna.md)
* [Repeaters Nodes](meshcore/rak-based-repeaters-note.md)
* [Mounting Options](meshcore/repeater-mounting-options.md)

### Configuration
* [Flashing a companion node](meshcore/flash-companion-node.md)
* [Flashing a Repeater node](meshcore/flash-repeater-node.md)
* [Flashing a room server](meshcore/configure-room-server.md)
* [Recommended Repeater Build Instructions](meshcore/build-repeater-solar-rak-unify-box.md)
* MeshCore to Discord using Meshcore-HA
* [Compiling Wifi Firmware for Heltek v3](meshcore/heltec-v3-wifi-firmware.md)
* [Compiling RAK4631 firmware with a Custom Display](meshcore/rak-custom-display-firmware.md)

### MeshCore Packet Analyzer
* [Overview](meshcore/packet-capture-overview.md)
* [Add a Companion Listener](meshcore/packet-capture-companion-listener.md)
* [Add a Standalone Listener](meshcore/packet-capture-standalone-repeater-listener.md)

### Ottawa Deployment
* [Repeaters & Coverage](meshcore/repeaters-and-coverage.md)
* [Frequency Settings](meshcore/frequency-settings-meshcore.md)
* [Wanted Repeater Locations](meshcore/wanted-repeater-locations.md)

## Meshtastic
The Meshtastic section is a work-in-progress 

* [Getting Started](meshtastic/getting-started.md)
* [Frequency Settings](meshtastic/frequency-settings.md)

## Useful Resources
* [Austin Mesh](https://www.austinmesh.org/) – Useful information and real-world testing of mesh nodes  
* [Cold Weather Charging of Lithium-Ion Batteries](https://yycmesh.com/2025/04/19/cold-weather-charging-of-lithium-ion-batteries-real-world-lessons-from-the-meshtastic-community/) – A great write-up on repeater performance in extreme cold with LiPos  

----
*This wiki is maintained by the Greater Ottawa Mesh Enthusiasts to provide information and track deployments.*
