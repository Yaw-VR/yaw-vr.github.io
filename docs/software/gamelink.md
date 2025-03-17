# Game Link

**Game Link** is a specialized, free tool designed to connect VR games seamlessly with Yaw VR motion simulators. It simplifies the setup process, allowing users to connect games with just a few clicks, without additional costs.
**Note:** Game Link can be used with a Yaw VR Motion Simulator or the [Yaw VR Emulator](./yawvremu.md).

## Key Features:

1. **Game Integration**: Supports numerous popular VR and PC games, including *Microsoft Flight Simulator*, *Assetto Corsa*, *Dirt 2*, and *Elite Dangerous*. If your game isn't supported, you can request integration from the developers.
2. **User-Friendly Setup**: Simply start the simulator, launch Game Link, and play your desired game. The tool also supports motion customization.
3. **Advanced Controls**: Adjust motion parameters like smoothing inputs, amplifying vibrations, and configuring LED lighting effects on the simulator.
4. **Free and Flexible**: The software is free to download and use, with ongoing updates expanding game compatibility. It includes SDKs for Unity and Unreal, enabling native support in games.

Download via Steam at: <a href="https://store.steampowered.com/app/3376270/Game_Link/" target="_blank">Yaw VR Game Link</a>.

## Getting Started

1. **Turn On Your Simulator**: Start your Yaw VR simulator or launch the [Yaw VR Emulator](./yawvremu.md).
2. **Open Game Link**: Launch the Game Link application.
3. **Connect to Your Simulator**: In the Device Selection section, connect to your simulator.
4. **Select a Game**: Choose a game from the list of supported titles.
5. **Access Additional Settings**: Configure settings for the selected game plugin.

## Main Sections

### Simulators

Connect to your Yaw VR motion simulator.

### Games

Lists games with motion support profiles.

### Description

Details about the currently selected game plugin, including options to:

- Start Plugin
- Recenter Yaw
- Calibrate (parked position)
- Start Device

### Motion & Vibration

Fine-tune the motion experience by mapping telemetry values to simulator axes and vibrations.

### Lights

Configure LED lighting effects based on the game or specific events.

### Arcade Buttons (Arcade Edition Simulators Only)

Map actions to arcade buttons for enhanced game-play.

### Simulator Settings

Adjust settings like power, pitch, roll, limited yaw, and vibration.

- Power, for motors (suggested value 30)
- Pitch forward  (default 30)
- Pitch backward (default 30)
- Roll (default 30)
- Limited Yaw
    - Enabled (default unselected)
    - Degrees (default 180)
- Vibration (default unselected)

### Input Monitor

View incoming data for mapped telemetry values and simulator outputs.

### USB

Bind USB axes to outputs for games lacking telemetry support, allowing customization of the simulation experience.

### Motion Compensation

Control motion compensation applied to the simulator.

### Game Plugins

Manage available game plugins, including installation and updates.

### Settings

Configure various options like anti-jump, vibration, convergent limit, anti-rollover, input commands, and miscellaneous settings for a tailored experience.

- Anti Jump (YAW)
    - Enabled (default selected)
    - Jump threshold (default 35)
- Vibration & Smartplug
    - Send vibration outputs to device (default selected)
    - Send smartplug output to device (default selected)
- Convergent Limit (default unselected)
- Anti Rollover
    - Pitch (default selected)
    - Roll (default selected)
- Input commands (trigger device commands via USB devices)
    - Device Start/Stop
    - Device Start
    - Device Stop
    - Device Park
    - Start Favorite
    - Recenter Yaw
- Miscellaneous
    - Check updates on startup (default selected)
    - Automatically launch Steam games (default selected)
    - Show splash (default selected)
    - Try to connect automatically (default selected)
    - Start device with delay (default selected)
    - Manage VirtualHere (default selected)
    - Stop plugin when game exits (default selected)
    - Exit on window close (default unselected)
    - Autostart plugin when game exits (default selected)
    - LED Offset (default 0)
    - USB Hz (default 50)
    - Change Language
