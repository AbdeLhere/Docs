---
cover: ../../.gitbook/assets/76B9617C-ADBF-493A-B1BD-33EE902BC4E2.jpg
coverY: 0
---

# QB Readme

## Overview

The Custom Pause Menu Script is designed for FiveM servers to provide a highly customizable pause menu. It integrates QBCore framework and supports a range of notification systems and sound effects. This guide will walk you through installation, configuration, usage, troubleshooting, and additional support.

## Useful Links

* [Join Our Discord](https://discord.gg/jgM5jW3rrN)
* [Visit Our Tebex Store](https://0resmonclub.tebex.io)
* [Donations](https://paypal.me/ablframework?country.x=FR\&locale.x=fr\_FR)

## Features

* **Framework Compatibility**: Works with QBCore framework and ESX framework.
* **Custom Notifications**: Multiple notification systems supported, including OX, okokNotify, BrutalNotify, and DefaultESX, DefaultESX.
* **Sound Effects**: Customizable sounds for menu actions (opening, closing, map interactions).
* **Item-Based Map Access**: Option to require a specific item to access the map.
* **Camera Adjustments**: Automatic camera view changes based on player status (in vehicle or walking).
* **Command and UI Customization**: Set up commands or keybind to open the menu and adjust UI settings.
* **Player Information**: Shows player details like name, job, cash, bank, phone, birthdate and nationality.
* **Server Information**: Displays server name, country, creation date, server owners, and staff number.
* **Disconnect Option**: Players can easily disconnect using the "Disconnect" button, which provides a user-friendly confirmation message and a pleasant farewell note when they quit.

## Installation

### Step-by-Step Installation

1. **Download the Script**:
   * Obtain the script files from the repository or source provided.
2. **Place the Script in Server Directory**:
   *   Move the script files to your FiveM server’s resources directory. For example:

       ```plaintext
       resources/[your_resource_folder]/abl-pausemenu-qb/
       ```
3. **Add to Server CFG**:
   * Open your `server.cfg` file.
   *   Add the following line to ensure the script is loaded and started:

       ```plaintext
       ensure abl-pausemenu-qb
       ```
4.  **Add Map Item ( Optional )**:

    * ( esx legacy )

    ```sql
    INSERT INTO items (name, label, weight) VALUES ('maptablet', 'Map Tablet', 1); 
    ```

    * ( old qb )

    ```lua

    ['maptablet'] = {
      ['name'] = 'maptablet',
      ['label'] = 'Map Tablet',
      ['weight'] = 1000,
      ['type'] = 'item',
      ['image'] = 'maptablet.png',
      ['unique'] = false,
      ['useable'] = true,
      ['shouldClose'] = true,
      ['combinable'] = nil,
      ['description'] = 'A tablet with map functionality' },
    ```

    * ( new qb )

    ```lua
      maptablet = { name = 'maptablet', label = 'Map Tablet', weight = 1000, type = 'item', image = 'maptablet.png', unique = false, useable = true, shouldClose = true, description = 'A tablet with map functionality' },
       
    ```

    \- ( ox inventory)

    ```lua
      ['maptablet'] = {
        label = 'Map Tablet',
        description = "A tablet with map functionality",
        weight = 30,
        stack = false
      },
    ```
5. **Restart the Server**:
   * Restart your FiveM server to apply the changes.

## Configuration

### Editing the Configuration File

1. **Open `config.lua`**:
   * Navigate to the `config.lua` file located in the script’s directory.
2. **Adjust the Configuration Parameters**:
   * Modify the configuration values according to your server's requirements.

#### Example Configuration

```lua
Config = {}

Config.System = {
    Debug = {
        UseDebug = 'no',
    },
    Framework = {
        Core = 'QBCore',        
        FolderName = 'qb-core',
    },
    Notify = {
        NotifyType = 'OX',
        NotifyTime = 1500, 
        UseFor = {
            WhenUIMenuOpen = { string = 'no', type = 'success' },
            WhenUIMenuClose = { string = 'no', type = 'success' },
            WhenSettingsOpen = { string = 'no', type = 'success' },
            WhenMapOpen = { string = 'yes', type = 'success' },
            WhenNoMapItem = { string = 'yes', type = 'error' },
            WhenNoTabletItem = { string = 'yes', type = 'success' },
        }
    },
}

Config.Options = {
    UIMenu = {
        Sounds = {
            PopUpSoundOpen = 'no', 
            PopUpSoundClose = 'no', 
            MapPaperSound = 'yes', 
            SettingsSound = 'no'    
        },
        Command = {
            UseCommand = 'yes',      
            CommandName = 'PauseMenu',
        },
    },
    MapItem = {
        NeedItemForMap = 'yes', 
        ItemName = 'tablet',     
        CloseUIIfNoItem = 'yes', 
    },
    Camera = {
        InVehicle = 'yes', 
        Walking = 'yes'    
    },
    OnNUIStart = function() 
    end,
    OnNUIClose = function() 
    end
}

Config.Lang = {
    QuitMessage = 'You have left! We hope you enjoyed and liked our custom server!',
    WhenUIMenuOpen = 'Menu Opened!',
    WhenUIMenuClose = 'Menu Closed!',
    WhenSettingsOpen = 'Settings Opened!',
    WhenMapOpen = 'Map Opened! Find your destinations.',
    WhenNoTabletItem = 'You do not have the Tablet item!',
    NoMapItem = 'You do not have the Map item!',
}
```

## FAQ

### Why are notifications not appearing in the game?

* **Notification Type**: Ensure that `Config.System.Notify.NotifyType` is set to a valid notification system that is installed on your server.
* **Notification System**: Confirm that the notification system’s export functions are correctly implemented and accessible.

### The map item requirement isn’t working. What should I check?

* **Item Name**: Verify that `Config.Options.MapItem.ItemName` matches the exact name used in your inventory system.
* **Inventory Check**: Ensure that the `CheckMapItem` function correctly checks for the item in the player’s inventory and that the item exists.

### How do I contribute to the script or report bugs?

* **Contributing**: We appreciate contributions! If you have suggestions or improvements, please reach out to us directly through our official ([Discord Server](https://discord.gg/jgM5jW3rrN)).
* **Reporting Bugs**: Since this is a paid script, please report any issues by opening a ticket in our ([Discord Server](https://discord.gg/jgM5jW3rrN)). Provide detailed information about the bug, including steps to reproduce, error messages, and any relevant configuration.
* **Resale and Redistribution**: Please note that this script is paid, and you do not have permission to resell, repost, or leak it for free. Unauthorized distribution is strictly prohibited.

### Usage

### Opening and Closing the Menu

* **Command**: Use the command specified in `Config.Options.UIMenu.Command.CommandName` (default: `/PauseMenu`) to open the menu.
* **Control Key**: By default, the menu can be toggled with the `ECS` key. Ensure that the key binding does not conflict with other controls.

### Notifications and Sounds

* **Notifications**: Configure the types of notifications and their settings in the `Config` table.
* **Sounds**: Adjust sound settings for various menu actions in the `Config.Options.UIMenu.Sounds` table.

### Item-Based Map Access

* If `Config.Options.MapItem.NeedItemForMap` is set to `'yes'`, players must have the specified item in their inventory to access the map. Ensure the item name matches exactly with the inventory item used in your server.

### Camera Adjustments

* The script can automatically adjust the camera view when the menu is opened based on whether the player is in a vehicle or walking. Configure this in `Config.Options.Camera`.
