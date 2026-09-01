---
cover: ../../.gitbook/assets/FST Enhanced Minimap V2.jpg
coverY: -481.6592592592593
coverHeight: 623
layout:
  width: default
  cover:
    visible: true
    size: full
    mask: none
  title:
    visible: false
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: false
  tags:
    visible: true
  actions:
    visible: true
---

# fst-enhanced-minimap-v2

## <mark style="color:yellow;">**Check sub pages for more⚠️**</mark>

{% stepper %}
{% step %}
### **Required step before starting.**

* Remove any old minimap scripts from your server resources.
* Download and ensure ox\_lib _before_ this script in your `server.cfg`.
* Drag and drop the script into your resources folder (do not rename the folder).
* _(Optional)_ Install [fst\_default\_minimap](https://github.com/AbdeLhere/fst_default_minimap) if you want the default Atlas minimap.
{% endstep %}

{% step %}
### **Configure Core Settings**

{% content-ref url="admin-system.md" %}
[admin-system.md](admin-system.md)
{% endcontent-ref %}

* Set `framework = 'standalone'` if you encounter framework issues.
* Enable `cayo perico` under the `customMaps` section if your server uses Cayo Perico.
* Review admin permissions in the config if you want to restrict map configuration access to admins only.
{% endstep %}

{% step %}
### Troubleshooting&#x20;

**Fix Minimap Pulsing Issue :**&#x54;roubleshooting radar zoom.If your minimap pulses or flashes, disable `radarZoom` in your config by setting `enabled = false`:Lua

```lua
radarZoom = {
    enabled = false, -- Set to false if your HUD already handles radar zoom
    level   = 1300,
}
```
{% endstep %}
{% endstepper %}
