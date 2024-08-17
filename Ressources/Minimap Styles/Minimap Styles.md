## __Description 🔑__

I am thrilled to present my new collection of minimap designs for FiveM. This package includes over 40 different designs, each crafted across 5 unique templates. Each style comes as a single script featuring custom pause menu colors and a matching background color to complement the minimap. Additionally, we offer custom map creation tailored to your ideas, with personalized zone names and colors.

## __Useful Links 😊__

- [Join Our Discord](https://discord.gg/jgM5jW3rrN)
- [Visit Our Tebex Store](https://0resmonclub.tebex.io)
- [Donations](https://paypal.me/ablframework?country.x=FR&locale.x=fr_FR)

## __Installation / Information 📖__

### Step 1: Remove Old Minimap Script
- Start by removing any old minimap script from your resources folder.

### Step 2: Cleanup
- Open **Visual Studio Code**.
- Press `CTRL + K + O` to open a folder.
- Select your server folder and press `Open`.
- Press `CTRL + SHIFT + F` to search for the following lines:  
   - `SetMapZoomDataLevel`
   - `SetRadarZoom`
   - `SetRadarAsInteriorThisFrame`  
- Remove these lines if found, **but do not remove them from the new script!**

### Step 3: Ensuring the New Script
- Drag and drop the new resource into your resources folder.
- Open your `server.cfg` file and add the following line after your framework, replacing `"script-name"` with your actual script name (e.g., `abl-minimap-X8-OP`):

```lua
ensure "script-name"
```

- Restart your server.

### Step 4: Configuration
- You can adjust the background opacity in `Config.Options.opacity` (Max: 200, Min: 0).
- Pause Menu colors can be edited in `Config.Options.RedGreenBlueAlpha`. You can use the [RGBA Color Picker](https://rgbacolorpicker.com/) to choose your preferred colors.
- **Note:** If you change colors, please avoid modifying `["ALPHA"] = 0.8`.
- To customize titles, refer to `Config.Options.Header`.

Here's a sample configuration snippet:

```lua
Config.Options = {
    opacity = 90, -- Change background opacity
    RedGreenBlueAlpha = {
        LINE = { -- Line color over options
            ["RED"] = 255,
            ["GREEN"] = 0,
            ["BLUE"] = 0,
            ["ALPHA"] = 0.8,
        },
        STYLE = { -- Pause Menu options color
            ["RED"] = 112,
            ["GREEN"] = 0,
            ["BLUE"] = 2,
            ["ALPHA"] = 0.8,
        },
        WAYPOINT = { -- Waypoint color
            ["RED"] = 255,
            ["GREEN"] = 0,
            ["BLUE"] = 0,
            ["ALPHA"] = 0.8,
        },
    },
    Header = {
        ["TITLE"] = "Server Name Menu",
        ["SUBTITLE"] = "The Beautiful City",
        ["MAP"] = "Map",
        ["GAME"] = "Exit Game",
        ["LEAVE"] = "Return to Server List",
        ["QUIT"] = "Return to Desktop",
        ["INFO"] = "Information",
        ["STATS"] = "Statistics",
        ["SETTINGS"] = "Settings",
        ["GALLERY"] = "Gallery",
        ["KEYBIND"] = "Main Keybinds",
        ["EDITOR"] = "Rockstar Editor",
        ["SERVER_NAME"] = "Server Name",
        ["SERVER_TEXT"] = "Welcome to Our City",
        ["SERVER_DISCORD"] = "discordlink.gg"
    }
}
```
