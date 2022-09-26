---
description: Toggle extras on the fly with hotkeys.
---

# 🎮 Extra Controls

## Introduction

The "extra\_controls" plugin handles specific extra toggling on demand using key bindings. The allows players the ability to toggle spotlights, light cuts, scene lights conveniently without navigating through existing menus. Controls can be set by default or left disabled, if `allow_custom_controls` is set to true, players can change each control combo and key in game through LVC menu.

<figure><img src="https://camo.githubusercontent.com/7fcb8ee3d541d0287bd197a9724976b482db5083de3260cddecd07ec07e8f71b/68747470733a2f2f692e6779617a6f2e636f6d2f32613235336232383539376631373033336364653633656338643937336165332e6a7067" alt=""><figcaption></figcaption></figure>

## Configuration

1. Ensure that `plugins_installed` is set to true in `lvc/SETTINGS.lua`.
2. Open the SETTINGS.lua located in `/plugins/extra_controls`. Adjust settings to your liking.
3.  Determine a set of controls/combos that players can use. Configure the EXTRA\_CONTROLS table to your liking.\
    List of Keys**:** [CFX Game Reference - Controls](https://docs.fivem.net/docs/game-references/controls/)

    _Example:_

    ```lua
    CONTROLS = {
    	-- COMBOS = { <list of index/key ID of approved combo-keys> }, 
    	-- KEYS = { <list of index/key ID of approved toggle keys> }
    	COMBOS = { 326, 155, 19, 349 },    --LCTRL, LSHIFT, LALT, TAB
    	KEYS = { 187, 188, 189, 190, 20 }  -- ARROW DWN, UP, LFT, RGT, Z
    }
    ```
4.  Configure the EXTRA\_CONTROLS table to your liking. \
    _Example:_

    ```lua
    EXTRA_CONTROLS = {
    	['DEFAULT'] = { 	},	
    	['LAPD'] = { 
    			--  	{ '<name>', Extras = {<extras table>}, Combo = <default combo>, Key = <default key>, (opt.) Audio = < button soundFX> }
    				{ Name = 'Front Cut', Extras = {add = 8, remove = 9, repair = true}, Combo = 155, Key = 20, Audio = true }, 
    				{ Name = 'Scene Lights', Extras = {toggle = 9, repair = true}, Combo = 349, Key = 20, Audio = true }, 
    				{ Name = 'Pass. Spot Light', Extras = {add = 3, remove = 4, repair = true}, Combo = 326, Key = 20, Audio = false }, 
    	},	
    	['so3'] = { 
    			--  	{ '<name>', Extras = {<extras table>}, Combo = <default combo>, Key = <default key>, (opt.) Audio = < button soundFX> }
    				{ Name = 'Test', Extras = {add = 4, remove = 9, repair = true}, Combo = 155, Key = 20, Audio = true }, 
    				{ Name = 'Test2', Extras = {toggle = 5, repair = true}, Combo = 349, Key = 20, Audio = true }, 
    				{ Name = 'Test3', Extras = {add = 6, remove = 7, repair = true}, Combo = 326, Key = 20, Audio = false }, 
    	},
    }
    ```

{% hint style="warning" %}
Every default `Combo` and `Key` assignment need to be present at a minimum in the CONTROLS table.
{% endhint %}

### Extras Table

#### **Toggle**

A toggle key will toggle a single extra on trigger or multiple extra if a table is passed in.

* Single Example: `Brake = { toggle = 1 }`
* Multiple Example: `Brake = { toggle = { 1, 2, 3, ... n } }`

#### **Add & Remove**

An add and remove key will add the passed extra(s) on trigger and remove passed extras(s) on trigger. When the control is pressed again, the behavior will reverse adding the removed extra(s) and removing the added extra(s).

* Single Example: `Brake = { add = 1, remove = 2 }`
* Multiple Example: `Brake = { add = { 1, 3 }, remove = { 2, 4 } }`

#### **Repair Flag**

A repair flag can optionally be added for higher poly extras. GTA will set extras of low poly items without repairing the vehicle, however for things like spotlights, lightbars, etc. the repair flag may need to be set. By default `repair` is set to disabled, to override add `repair = true` somewhere inside the desired trigger table.

* Examples:
  * `Brake = { toggle = 1, repair = true }`
  * `Takedowns = { add = { 5 }, remove = { 6 }, repair = true }`

#### Controls

* Combo: _combokey_ to be pressed in addition to _key_ in order to activate profile. `Combo = 0` to disable the need for a combo key.
* Key: _control_ to be pressed with _combokey_ (if set) in order to activate profile.

#### Audio

The audio flag determines if the plugin plays a button press soundfx (like heard when toggling siren) when the extra\_control profile is toggled.

#### Finished ✅ , configure your personal settings in game under 'Plugins/Extra Control' menu.
