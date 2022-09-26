---
description: Debugging and advanced configuration functionality.
---

# Advanced Configuration

### Debug Mode

To temporarily toggle _debug mode_ use chat command `/lvcdebug` this resets on resource restart. For persistent debug mode use convar below.

### **Resource Convars (fxmanifest.lua)**

* `experimental` will mute experimental messages for server console.
* `debug_mode` increases console logging for client, prints \<gameName> of vehicle if no profile was found.

{% hint style="info" %}
Toggling these require the `refresh` command to be ran first, then restart the resource for changes to take effect.
{% endhint %}

### Custom HUD

The in game siren controller display or heads-up-display UI can be modified to your liking, you will need an understanding of HTML, Javascript, and NUI.&#x20;

{% hint style="info" %}
Support is limited in this area.
{% endhint %}

### Custom Audio Schemes

Custom front end sound effects can be added. Create a new folder in `/UI/sounds` with the desired name of your scheme.

{% hint style="warning" %}
Sound scheme names cannot have any spaces in them.
{% endhint %}

Add scheme name to `button_sfx_scheme_choices` in SETTINGS.lua.
