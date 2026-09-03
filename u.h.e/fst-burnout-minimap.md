---
description: >-
  a dark, fiery custom minimap featuring a burnt-out urban aesthetic, detailed
  roads, and glowing orange accents.
cover: ../.gitbook/assets/burnout minimap thumb.jpg
coverY: -492.44444444444446
coverHeight: 276
layout:
  width: default
  cover:
    visible: true
    size: full
    mask: radial
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
---

# fst-burnout-minimap

<figure><img src="../.gitbook/assets/burnout minimap thumb.jpg" alt=""><figcaption></figcaption></figure>

### Requirements

{% hint style="warning" %}
Optional: `ox_lib` (only required if the `/mapcolors` command is enabled)
{% endhint %}

### Installation

1. Place the resource inside your server resources folder.
2. Make sure the folder name is exactly:

```lua
fst_burnout_minimap
```

3. Add the resource to your `server.cfg`:

```cfg
ensure fst_burnout_minimap
```

4. (Optional) Install and start `ox_lib` before this resource if you want to use the `/mapcolors` command.
5. Adjust `config.lua` to your liking and restart the resource.

### Using with Enhanced Minimap

If you own **fst\_enhanced\_minimap** and want to use the Old Paper overlays with it:

#### Setup

1. Set compatibility mode in `config.lua`:

```lua
Config.using_the_enhanced_minimap = true
```

2. Ensure both resources:

```cfg
ensure fst_enhanced_minimap
ensure fst_burnout_minimap
```

3. Restart your server.

The Old Paper Minimap will only provide its textures and overlays while Enhanced Minimap handles all UI, radar, tablet, and player features.

{% hint style="info" %}
If you are not using Enhanced Minimap:
{% endhint %}

```lua
Config.using_the_enhanced_minimap = false
```

The Old Paper Minimap will run independently with all features enabled.

### Config

```lua
Config = {}
Config.debug = false                 -- Set to false to disable debug messages
Config.enable_map_zoom_levels = true -- Enable different map zoom levels

--========================================================================================--
--  ENHANCED MINIMAP COMPATIBILITY
--  Set to true if you're using fst_enhanced_minimap alongside this resource
--
--  When enabled:
--  - All Burnout Minimap features are DISABLED (zoom, radar, blur, pause menu, commands, tile system)
--  - Only the overlay textures in the stream folder are provided
--  - Enhanced Minimap detects and loads Burnout textures automatically
--  - Use Enhanced Minimap's tablet to toggle Burnout overlays on/off
--
--  When disabled (false):
--  - Burnout Minimap runs standalone with all features enabled
--========================================================================================--
Config.using_the_enhanced_minimap = false

Config.ZoomLevels = {
  { index = 0, zoomScale = 0.96,  zoomSpeed = 0.9, scrollSpeed = 0.08, tilesX = 0.0, tilesY = 0.0 },
  { index = 1, zoomScale = 1.6,   zoomSpeed = 0.9, scrollSpeed = 0.08, tilesX = 0.0, tilesY = 0.0 },
  { index = 2, zoomScale = 8.6,   zoomSpeed = 0.9, scrollSpeed = 0.08, tilesX = 0.0, tilesY = 0.0 },
  { index = 3, zoomScale = 12.3,  zoomSpeed = 0.9, scrollSpeed = 0.08, tilesX = 0.0, tilesY = 0.0 },
  { index = 4, zoomScale = 24.3,  zoomSpeed = 0.9, scrollSpeed = 0.08, tilesX = 0.0, tilesY = 0.0 },
  { index = 5, zoomScale = 55.0,  zoomSpeed = 0.0, scrollSpeed = 0.1,  tilesX = 2.0, tilesY = 1.0 },
  { index = 6, zoomScale = 450.0, zoomSpeed = 0.0, scrollSpeed = 0.1,  tilesX = 1.0, tilesY = 1.0 },
  { index = 7, zoomScale = 4.5,   zoomSpeed = 0.0, scrollSpeed = 0.0,  tilesX = 0.0, tilesY = 0.0 },
  { index = 8, zoomScale = 11.0,  zoomSpeed = 0.0, scrollSpeed = 0.0,  tilesX = 2.0, tilesY = 3.0 },
}

Config.Radar = {
  zoom = {
    enabled = true,        -- Enable automatic radar zoom
    on_vehicle = 1000,     -- Zoom level when in vehicle (default: 1000)
    on_foot = 1100,        -- Zoom level when on foot (default: 1100)
    check_interval = 1000, -- How often to check zoom in ms (default: 1000)
  },
  disable_blur = true,     -- Disable the blur effect when loading minimap (recommended: true)
}

Config.PauseMenu = {
  enable_color_picker = true, -- Allow players to change colors with a command
  command = "mapcolors",      -- Command to open color picker (/mapcolors)

  -- Default colors (RGB format: 0-255) - Burnout theme
  colors = {
    line = { enabled = true, red = 255, green = 114, blue = 24, alpha = 255 },      -- Burnt Orange (western leather)
    background = { enabled = true, red = 94, green = 28, blue = 8, alpha = 200 }, -- Dark Brown (saddle leather)
    pause_bg = { enabled = true, red = 94, green = 28, blue = 8, alpha = 200 },    -- Light Brown (desert sand)
    waypoint = { enabled = true, red = 255, green = 114, blue = 24, alpha = 255 },  -- Goldenrod (western gold)
  },
}

Config.overlays = {
  -------------------
  --- MAP THEMES ---
  -------------------
  mainmaptheme = {
    enabled = true, -- Main map theme
    opacity = 100,  -- Opacity/alpha value (0-100, default: 100)
  },
  -------------------
  --- MAP EXTENSIONS ---
  -------------------
  roxwood = {
    enabled = true, -- Roxwood map extension
    opacity = 100,  -- Opacity/alpha value (0-100, default: 100)
  },
  cayo_perico = {
    enabled = true, -- Cayo Perico map
    opacity = 100,  -- Opacity/alpha value (0-100, default: 100)
  },
  cayoBridge = {
    enabled = false, -- Cayo Bridge V3
    opacity = 100,   -- Opacity/alpha value (0-100, default: 100)
  },
  cayoBridge1 = {
    enabled = false, -- Cayo Bridge V1
    opacity = 100,   -- Opacity/alpha value (0-100, default: 100)
  },
  cayoBridge2 = {
    enabled = false, -- Cayo Bridge V2
    opacity = 100,  -- Opacity/alpha value (0-100, default: 100)
  },
  cayoBridge4 = {
    enabled = false, -- Cayo Bridge V4
    opacity = 100,   -- Opacity/alpha value (0-100, default: 100)
  },
}

Config.load_order = {
  "mainmaptheme", -- Main map theme - loads first (base layer)
  "roxwood",      --
  "cayo_perico",  --
  "cayoBridge",   --
  "cayoBridge1",  --
  "cayoBridge2",  --
  "cayoBridge4",  -- Loads last (top layer)
}

    opacity = 100,   -- Opacity/alpha value (0-100, default: 100)
  },
  cayo_bridge1 = {
    enabled = false, -- Cayo Bridge V1
    opacity = 100,   -- Opacity/alpha value (0-100, default: 100)
  },
  cayo_bridge2 = {
    enabled = false, -- Cayo Bridge V2
    opacity = 100,   -- Opacity/alpha value (0-100, default: 100)
  },
  -------------------
  --- OVERLAYS  ---
  -------------------
  postales_4 = {
    enabled = false, -- 4-digit postal codes
    opacity = 50,    -- Opacity/alpha value (0-100, default: 100)
  },
  ocrp_postales = {
    enabled = true, -- OCRP postal codes
    opacity = 50,   -- Opacity/alpha value (0-100, default: 100)
  },
  utr_routes = {
    enabled = false, -- Urban/rural route markers
    opacity = 100,   -- Opacity/alpha value (0-100, default: 100)
  },
  zone_names = {
    enabled = false, -- Zone/district names
    opacity = 100,   -- Opacity/alpha value (0-100, default: 100)
  },
  poi_icons = {
    enabled = false, -- Points of interest icons
    opacity = 100,   -- Opacity/alpha value (0-100, default: 100)
  },
  map_key = {
    enabled = false, -- Map key/legend
    opacity = 100,   -- Opacity/alpha value (0-100, default: 100)
  },
}

Config.load_order = {
  "mainmaptheme",  -- Main map theme - loads first (base layer)
  "postales_4",    --
  "ocrp_postales", --
  "utr_routes",    --
  "poi_icons",     --
  "map_key",       --
  "roxwood",       --
  "cayo_perico",   --
  "cayo_bridge",   --
  "cayo_bridge1",  --
  "cayo_bridge2",  --
  "zone_names",    -- Loads last (top layer)
}

```
