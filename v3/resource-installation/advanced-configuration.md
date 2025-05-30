---
description: Debugging and advanced configuration functionality.
---

# Advanced Configuration

### Debug Mode

To temporarily toggle _debug mode_ use chat command `/lvcdebug` this resets on resource restart. For persistent debug mode use convar below.

### **Resource Convars (fxmanifest.lua)**

* `beta_checking` enables beta version notifications to server console.
* `experimental` will mute experimental messages for server console.
* `debug_mode` increases console logging for client, prints \<gameName> of vehicle if no profile was found.

{% hint style="info" %}
Changing covars require the `refresh` command to be ran first, then restart the resource for changes to take effect.
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

**The relevant attributes are:&#x20;**_**left**_**,&#x20;**_**top**_**, and&#x20;**_**transform-origin**_**.**

* _left_ determines how far in percentage of the screen resolution should the HUD be placed from the left edge. If you wanted to right align the HUD you could change this to `right: XX%`, 0% being against the right edge of the display.
* _top_ determines how far down from the top the HUD should be placed.
* _transform-origin_ attribute determines which way the HUD should expand on size adjustment. For a bottom right aligned HUD you would want the transform-origin to be `right bottom`. This ensures that the HUD does not expand outside of the screen space.

### Custom Audio Schemes

Custom front end sound effects can be added. Create a new folder in `/UI/sounds` with the desired name of your scheme.

{% hint style="warning" %}
Sound scheme names cannot have any spaces in them.
{% endhint %}

Add scheme name to `button_sfx_scheme_choices` in SETTINGS.lua.
