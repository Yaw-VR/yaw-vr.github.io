# Game Link

## Overview

**Game Link** is a free specialized tool designed to seamlessly connect VR games to Yaw VR motion simulators, enabling immersive gaming experiences with minimal setup. Unlike middleware solutions like SimTools, Yaw VR Game Link simplifies the process, allowing users to connect games to the simulator with a few clicks and without additional cost.

**Note:** Game Link can be used with a Yaw VR Motion Simulator, or the [Yaw VR Emulator](./yawvremu.md).

### Key Features:

1. **Game Integration**: Supports a growing list of popular VR and PC games, such as *Microsoft Flight Simulator*, *Assetto Corsa*, *Dirt 2*, *Elite Dangerous*, and more. If your game isn’t supported, you can request integration from the developers.
2. **User-Friendly Setup**: Users simply start the simulator, launch Game Link, and then play their desired game. The tool also supports motion customization, including yaw, pitch, roll, and other dynamics.
3. **Advanced Controls**: It allows adjustment of motion parameters, such as smoothing inputs, amplifying vibrations, and even configuring LED lighting effects on the simulator.
4. **Free and Flexible**: The software is free to download and use, with ongoing updates to expand game compatibility.

The engine also provides SDKs for Unity and Unreal, enabling developers to build native support into their games.

For more information, check out the official page: <a href="https://www.yawvr.com/game-link" target="_blank">Yaw VR Game Link</a>.

## How to use

1. Turn on your Yaw VR simulator, or start the [Yaw VR Emulator](./yawvremu.md)
2. Open Game Link
3. On the Device Selection section of Game Link sidebar connect to your simulator
4. Once connected you can select which game you would like to play from the Game Library section of Game Link
5. Once game is selected you can access additional settings from the Yaw Link sidebar

### Simulators

Allows you to connect to your simulator.

### Games

Lists games that have motion support profiles.

### Description

Details of the currently selected game plugin.

Allows you to:

- Start Plugin (of the currently selected game)
- Recenter Yaw
- Calibrate (parked position)
- Start Device

### Motion & Vibration

Control what telemetry value maps to what axis and vibration of the simulator. This allows for fine-tuning the motion experience to match the game's dynamics.

### Lights

Configure the LED lighting effects on your simulator based on the game or specific events within the game.

### Arcade Buttons (only Arcade Edition Simulators)

Configure arcade buttons on your simulator, allowing you to map specific actions to these buttons. This feature is available only on Arcade Edition simulators.

### Simulator Settings

Adjust settings specific of your simulator, these changes survive simulator restart.

- Power, for motors (suggested value 30)
- Pitch forward  (default 30)
- Pitch backward (default 30)
- Roll (default 30)
- Limited Yaw
    - Enabled (default unselected)
    - Degrees (default 180)
- Vibration (default unselected)

### Input Monitor

Shows incoming data for mapped telemetry values, and the outputs to the simulator

### USB

Bind USB axes to outputs in much the same way as plugins. Even for games that lack telemetry support, you can still effectively utilize the simulator by mapping actions like joystick triggers to effects such as rumble feedback. If a specific telemetry function is missing—such as firing guns on a plane—you can bind the relevant joystick input to an appropriate output, ensuring that your simulation remains functional and immersive.

Plugins and USB bindings can be used simultaneously, allowing for a highly customizable and versatile setup tailored to your needs.

### Motion Compensation

Control if and how how motion compensation is applied to the simulator.

### Game Plugins

Lists all available game plugins and allows you to install or update them.

Each plugin allows you to select the installed path of the related game.

### Settings

Settings for:

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
    - Manage Virtualhere (default selected)
    - Stop plugin when game exits (default selected)
    - Exit on window close (default unselected)
    - Autostart plugin when game exits (default selected)
    - LED Offset (default 0)
    - USB Hz (default 50)
    - Change Language