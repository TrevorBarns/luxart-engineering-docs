---
description: Debugging and advanced configuration functionality.
---

# 💻 Advanced Configuration

### Debug Mode

To temporarily toggle _debug mode_ use chat command `/lvcdebug` this resets on resource restart. For persistent debug mode use convar below.

### **Resource Convars (fxmanifest.lua)**

* `beta_checking` enables beta version notifications to server console.
* `experimental` will mute experimental messages for server console.
* `debug_mode` increases console logging for client, prints \<gameName> of vehicle if no profile was found.

{% hint style="info" %}
Toggling these require the `refresh` command to be ran first, then restart the resource for changes to take effect.
{% endhint %}

### Custom HUD

#### Custom Graphics

The in game siren controller display or heads-up-display UI can be modified to your liking, you will need an understanding of HTML, Javascript, and NUI.&#x20;

{% hint style="info" %}
Support is limited in this area.
{% endhint %}

#### Move Default HUD location

All HUD related functions/code is located in the UI folder. The default position of the HUD is set in `UI/html/style.css`.

```css
#sirenbox {
	display: none;
	position: absolute;
	overflow: hidden;
	width: 602px;
	height: 161px;
	left: 0%;
	top: 68%;
	transform-origin: left top;
	transform: scale(0.6);
	background-image: url("../textures/background.png");
}
```

**The relevant attributes are: **_**left**_**, **_**top**_**, and **_**transform-origin**_**.**

* _left_ determines how far in percentage of the screen resolution should the HUD be placed from the left edge. If you wanted to right align the HUD you could change this to `right: XX%`, 0% being against the right edge of the display.
* _top_ determines how far down from the top the HUD should be placed.
* _transform-origin_ attribute determines which way the HUD should expand on size adjustment. For a bottom right aligned HUD you would want the transform-origin to be `right bottom`. This ensures that the HUD does not expand outside of the screen space.

### Custom Audio Schemes

Custom front end sound effects can be added. Create a new folder in `/UI/sounds` with the desired name of your scheme.

{% hint style="warning" %}
Sound scheme names cannot have any spaces in them.
{% endhint %}

Add scheme name to `<SCHEMES>` object in VCF.

### Ace Menu Permissions

{% hint style="info" %}
__:date: Future Feature: estimated release 1.0.0-BETA
{% endhint %}

#### Set up VCF for Permission

To do this add an attribute to the associated menu item you would like to limit a profile's VCF.

```xml
<MENU>
	<Menu_Access Enabled='true'/>
	...
	<Toggle_Peer_Override Enabled="true" Permissions="true"/>	
	<Toggle_Local_Override Enabled="true" Permissions="true"/>
	...
	<Menu_Plugins Enabled="true"/>
</MENU>
```

In the example above, we've added `Permissions="true"` after the enable attribute. It is important to note that the `Enabled` attribute must be true, it acts as an end-all-be-all switch. Permissions can be added to any of the `<MENU>` elements, and are optional so you only need to add this attribute to the menu items you wish to limit access to.

#### Add Ace Config / Permissions Lines

```actionscript
add_ace builtin.everyone "LVC:Fleet.menu_access" allow
add_ace builtin.everyone "LVC:Fleet.menu_main_siren_settings" allow
add_ace builtin.everyone "LVC:Fleet.toggle_peer_override" allow
add_ace builtin.everyone "LVC:Fleet.toggle_local_override" allow
add_ace builtin.everyone "LVC:Fleet.toggle_airhorn_intrp" allow
add_ace builtin.everyone "LVC:Fleet.toggle_reset_standby" allow
add_ace builtin.everyone "LVC:Fleet.custom_tone_options" allow
add_ace builtin.everyone "LVC:Fleet.custom_manual" allow
add_ace builtin.everyone "LVC:Fleet.custom_auxiliary" allow
add_ace builtin.everyone "LVC:Fleet.toggle_park_kill" allow
add_ace builtin.everyone "LVC:Fleet.menu_hud_settings" allow
add_ace builtin.everyone "LVC:Fleet.toggle_hud" allow
add_ace builtin.everyone "LVC:Fleet.custom_backlight_mode" allow
add_ace builtin.everyone "LVC:Fleet.menu_audio_settings" allow
add_ace builtin.everyone "LVC:Fleet.toggle_radio" allow
add_ace builtin.everyone "LVC:Fleet.custom_scheme" allow
add_ace builtin.everyone "LVC:Fleet.toggle_clicks" allow
add_ace builtin.everyone "LVC:Fleet.custom_activity_reminder" allow
add_ace builtin.everyone "LVC:Fleet.menu_plugins" allow
```

Change the `builtin.everyone` to the ace group you'd like to authorize, just like any other resource.

{% hint style="info" %}
`Menu_Access` in both VCF and ace permissions controls the menu as a whole, so you don't need to add every menu item if you intend on disabling the menu entirely.
{% endhint %}
