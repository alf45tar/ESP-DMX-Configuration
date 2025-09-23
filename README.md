# ESP-DMX Configuration Utility  
**Professional lighting control interface**

The **ESP-DMX Configuration Utility** provides a graphical interface to remotely configure WiFi and DMX protocol parameters on ESP-DMX devices. Configuration is achieved by connecting to a target device, adjusting parameters, and uploading them as a configuration packet.  

## Device Management
**Tab: Device**

![Device](Screenshot%20Device.png)

### Device Connection

This section allows discovery and connection to ESP-DMX devices on your network.

- **Target IP Address**  
  Enter the IP address of the device or a broadcast address (e.g., `10.255.255.255`) to search.  

- **Discover Device**  
  Initiates a discovery request to locate available ESP-DMX units.  

- **Connection Status**  
  Displays whether the utility is successfully connected to a device.  

Once connected, the device is ready to accept configuration uploads.  

### Configuration Management

- **Upload Configuration**  
  Sends current settings (WiFi + DMX) to the connected device.  

### Art-Net Specific Commands
When using the **Art-Net protocol**, additional protocol-specific controls are available:

- **Cancel Merge**  
  Stops an ongoing Art-Net merge process.  

- **Clear Output**  
  Resets Art-Net output data.  

## 3. WiFi & IP Configuration
**Tab: Network**

![Network](Screenshot%20Network.png)

### WiFi Configuration
Define how the device connects to wireless networks:

- **Network Name (SSID)**: Enter the WiFi SSID.  
- **Password**: Enter the WiFi password.  
- **Connection Mode**:  
  - **Station Mode**: Connects to an existing WiFi network.  
  - **Access Point Mode (AP Mode)**: Creates its own WiFi network (fallback if station connection fails).  

### IP Configuration
Configure addressing for either Station or AP mode:

- **Use Static IP**: Option to disable DHCP and set a manual IP.  
- **Access Point Settings**:  
  - **AP IP Address**  
  - **AP Gateway**  
  - **AP Subnet Mask**  

**Important:**  
When WiFi credentials are updated and uploaded, the ESP-DMX device **must restart** to apply new settings.  

## 4. Protocol Configuration
**Tab: Protocol**

![Protocol](Screenshot%20Protocol.png)

Configure DMX protocol parameters and network transport options.

### Protocol Selection
- **Art-Net (Port 6454)** – Industry-standard Ethernet lighting protocol.  
- **sACN (E1.31, Port 5568)** – ESTA streaming protocol.  
- **Data Direction** – Select input (receive from console).  

### Network Mode
Defines how DMX data is distributed:  
- **Broadcast** – Sends to all devices on the network.  
- **Multicast** – Sends to a specific group address.  
- **Multicast IP Address** – Address for multicast mode.  
- **Network Target** – Defines broadcast/unicast target.  

### Universe Configuration
- **Art-Net Subnet**: 0–15  
- **Art-Net Universe**: 0–15  
- **Node Name**: Custom device identifier.  
- **RDM Support**: Enable/disable Remote Device Management protocol.  

---

## 5. Fallback Logic
To guarantee device accessibility:  
1. On startup, the ESP-DMX tries to connect in **Station Mode** using the last known SSID and password.  
2. If unsuccessful, it automatically switches to **Access Point Mode** with default credentials.  
3. From AP mode, a computer can connect and reconfigure WiFi or DMX settings.  

## 6. Typical Workflow
1. **Discover Device** or enter its IP manually.  
2. Connect and verify **Connected** status.  
3. Go to **Network** → configure WiFi and IP settings.  
4. Go to **Protocol** → set DMX protocol, universe, and network transport.  
5. Return to **Device** → upload configuration.  
6. If WiFi was changed, device restarts and reconnects using new settings.  
