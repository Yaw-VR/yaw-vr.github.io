# Yaw VR Emulator

## Overview

The Yaw VR Emulator is a software tool designed to simulate the functionality of a Yaw VR motion simulator. It allows developers and enthusiasts to test and develop VR applications without needing expensive hardware.

## Features

- **Local Network Discovery**: The emulator is discoverable on the local network, just like the real device.
- **Game Connectivity**: Games can connect to it for testing purposes.
- **TCP/UDP Commands**: Supports TCP and UDP commands, sends responses, and displays them on the screen.
- **State Display**: Shows the current state (Available, Connected, In Game).
- **3D Model View**: Displays a 3D simulator model from four different directions.
- **Motion Simulation**: Simulates motion based on input.
- **Rotation Limits**: Shows rotation limits.
- **SimTools Support**: Supports SimTools.

## Installation

### Prerequisites

- **Operating System**: Windows 10 or later, or Android.

### Steps

1. **Download and Install**: [Download Yaw VR Emulator](https://www.yawvr.com/downloads)

## Usage

Ensure that the device running the emulator is connected to the same network as the device you are connecting to the emulator.

If you experience issues with communication between the emulator and your game:

- Verify that your network/router allows sending TCP and UDP messages to the chosen ports.
- Adjust your firewall settings accordingly.

After starting the emulator, you can find its current TCP and UDP ports and IP address in the lower-left corner of the screen. The default configuration is as follows:

- **TCP Port**: 50020
- **UDP Port**: 50010

You can modify port numbers by changing the value of their fields.

## How to Control the Emulator

### Direct Command Control (Authenticated)

1. **Device Discovery:**
    - You can discover emulators on your local network by sending a `DEVICE_DISCOVERY` UDP broadcast message to IP address `255.255.255.255` and the emulator's UDP port.
    - The available emulators will respond with a `DEVICE_DISCOVERY_RESPONSE` command, providing their ID, name, TCP port, and status.

2. **Direct Targeting:**
    - You can directly connect to your emulator without going through the discovery phase if you already know its IP address and port.

3. **Connecting via TCP:**
    - Connect to the emulator's TCP server using a TCP client.

4. **Reserve the Emulator:**
    - Send a `CHECK_IN` command over TCP to reserve the emulator for your gaming session.
    - A `CHECK_IN_ANS` response will be sent back as confirmation.

5. **Start Rotation Tracking:**
    - Send a `START` command to inform the emulator that it should start following rotation values sent via UDP messages.
    - The emulator will respond with the same `START` command as confirmation.

6. **Set Rotation Values:**
    - Use `SET_POSITION` commands over UDP to send rotation values (euler angles) to the emulator.
    - The emulator's 3D simulator model will rotate according to these values, and it will respond with its current positions via `ACTUAL_POSITION` commands.

7. **Stop Rotation Tracking:**
    - Send a `STOP` command to stop following rotation commands until the next `START` command is issued.
    - The emulator will respond with the same `STOP` command as confirmation.

8. **Release Emulator for Others:**
    - Send an `EXIT` command to make the emulator available for other games.
    - The emulator will respond with the same `EXIT` command as confirmation.

### Using SimTools

1. **Enable SimTools in the Emulator:**
    - In the bottom-left corner of the emulator window, check the "Using SimTools" checkbox.

2. **Set Output Bit Range:**
    - Enter the output bit range that you have configured in the Interface Settings of SimTools.

## Sending TCP Commands

To send TCP commands, the game must connect to the emulator's TCP server. Each TCP command begins with a one-byte identifier, followed by bytes representing command parameters if any are required.

- **Data Types:**
    - Floating-point and integer number parameters are sent using 4 bytes.
    - String parameters are converted into a byte array using ASCII character encoding.
    - Number types must be sent in big-endian byte order. The YawVR Unity game package and the emulator handle the conversion to little-endian format on little-endian systems.

- **Default Response:**
    - If the emulator accepts a TCP command, it typically sends back the same message unless there is additional information required.

### TCP Commands Sent Only from the Game to the Emulator

1. **CHECK_IN**
    - **Command ID:** 0x30 (1 byte)
    - **Parameters:**
        - `int UDPListeningPort` (4 bytes)
        - `string gameName`
    - **Behavior:**
        - If available, the emulator accepts the connection and reserves it for the game.
    - **Response:**
        - Sends back a `CHECK_IN_ANS` command.

### TCP Commands Between the Emulator and the Game (Both Directions)

1. **START**
    - **Command ID:** 0xA1 (1 byte)
    - **Behavior:**
        - After receiving this command, the emulator starts following rotation orders from the game.
    - **Response:**
        - The same `START` command is sent back as confirmation.

2. **STOP**
    - **Command ID:** 0xA2 (1 byte)
    - **Behavior:**
        - Stops accepting rotation orders from the game.
    - **Response:**
        - The same `STOP` command is sent back as confirmation.

3. **EXIT**
    - **Command ID:** 0xA3 (1 byte)
    - **Behavior:**
        - Disconnects from the game and becomes available for other uses.
    - **Response:**
        - The same `EXIT` command is sent back as confirmation.

4. **SET_TILT_LIMITS**
    - **Command ID:** 0x40 (1 byte)
    - **Parameters:**
        - `int pitchForwardLimit` (4 bytes)
        - `int pitchBackwardLimit` (4 bytes)
        - `int rollLimit` (4 bytes)
    - **Behavior:**
        - Sets the tilt limits for the emulator.
    - **Response:**
        - The same command with accepted values is sent back as confirmation.

5. **SET_YAW_LIMIT**
   - **Command ID:** 0x70 (1 byte)
   - **Parameters:**
     - `int yawLimit` (4 bytes)
   - **Behavior:**
     - Sets the yaw limit for the emulator.
   - **Response:**
     - The same command with accepted value is sent back as confirmation.

### TCP Commands Sent Only by Emulator to Game

1. **CHECK_IN_ANS**
    - **Command ID:** 0x31 (1 byte)
    - **Parameters:**
        - `string answer`
    - **Behavior:**
        - Indicates the availability status.
        - If available, the response is "AVAILABLE".
        - If reserved by another game, the response includes details like the game name and IP address using the simulator.

2. **ERROR**
    - **Command ID:** 0xA5 (1 byte)
    - **Parameters:**
        - `string description`
    - **Behavior:**
        - Provides an error message detailing the issue encountered.

## Sending UDP Commands

UDP commands are ASCII-encoded strings.

### UDP Messages Sent from the Game to the Emulator

1. **DEVICE_DISCOVERY**
    - **Message:** "YAW_CALLING"
    - **Usage:** Broadcast message. When an emulator receives this command, it sends a `DEVICE_DISCOVERY_RESPONSE` back to the sender.

2. **SET_POSITION**
    - **Format:**
        - Yaw, pitch, and roll Euler angles in the format:
       ```
       "Y[000.00]P[359.99]R[342.54]"
       ```
    - **Constraints:**
        - Values range from 000.00 to 359.99.
        - Use 000.00 instead of 360.00.
    - **Response:** None

### UDP Messages Sent from the Emulator to the Game

1. **DEVICE_DISCOVERY_RESPONSE**
    - **Format:**
        - If available:
       ```
       "YAWDEVICE;” + /Simulator ID/ + ”;” + /Simulator name/ + ”;" + /TCP server port/ + ";AVAILABLE"
       ```
        - If reserved:
       ```
       "YAWDEVICE;” + /Simulator ID/ + ”;” + /Simulator name/ + ”;" + /TCP server port/ + ";RESERVED"
       ```

2. **ACTUAL_POSITION**
    - **Format:**
        - Yaw, pitch, and roll Euler angles in the format:
       ```
       "Y[000.00]P[359.99]R[342.54]"
       ```
    - **Constraints:**
        - Values range from 000.00 to 359.99.
        - Use 000.00 instead of 360.00.
