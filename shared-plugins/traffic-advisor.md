---
description: Quickly toggle rear traffic advisor patterns at the press of a button.
---

# 🔛 Traffic Advisor

## Introduction

The "traffic\_advisor" plugin is designed for extra toggling in order to activate certain rear traffic advisory lights. It works by placing light meshes under certain extras then toggling those extras to reveal or hide certain sirens.

{% hint style="danger" %}
**This requires the vehicle to already have working Traffic Advisor extras! LVC does not add a traffic advisor to vehicle which do not already have one.**
{% endhint %}

## Configuration

1. Ensure that `plugins_installed` is set to true in `/SETTINGS.lua`.
2. Open the SETTINGS.lua located in `/plugins/traffic_advisor`. Adjust settings to your liking.
3.  Now configure the TA\_ASSIGNMENTS table to your liking. The TA Assignments table is very dynamic an allows for multiple set up variations.\
    _Example:_

    {% code title="SETTINGS.lua" %}
    ```lua
    TA_ASSIGNMENTS = {
      ['DEFAULT'] = { },
      ['gameName'] = { 	lightbar = 3, 
    			left = { on = { add = 8, remove = 7, repair = true }, off = { add = {}, remove = { 7, 8 } } }, 
    			right = { on = { add = 7, remove = 8, repair = true }, off = { add = {}, remove = { 7, 8 } } }, 
    			middle = { on = { add = { 7, 8 }, remove = {}, repair = true }, off = { add = {}, remove = { 7, 8 } } }, 
    		},   
    }
    ```
    {% endcode %}

#### Lightbar

A lightbar key is used to ensure that the parent extra (a lightbar / TA bar) is present before toggling. This can be disabled by setting equal to '-1' if the TA lightbar is attached to the base model and not an extra.

#### On & Off

An on and off key will be called on TA state change.

#### Add & Remove

An add and remove key will add the passed extra(s) and remove passed extras(s) based on the TAs on/off state.

* Single Example: `on = { add = 1, remove = 2 }`
* Multiple Example: `on = { add = { 1, 3 }, remove = { 2, 4 } }`

{% hint style="info" %}
&#x20;Use `{}` to identify as unneeded. e.g. (`on = { add = 8, remove = {} }`)
{% endhint %}

#### Repair Flag

A repair flag can optionally be added for higher poly extras. GTA will set extras of low poly items without repairing the vehicle, however for things like spotlights, lightbars, etc. the repair flag may need to be set. By default `repair` is set to disabled, to override add `repair = true` somewhere inside the desired trigger table. This should only be needed when _adding_ extras.

* Examples:
  * `on = { add = 1, remove = {}, repair = true }`
  * `on = { add = { 5 }, remove = { 6 }, repair = true }`

{% hint style="success" %}
Finished, test your new traffic advisor integration in game.
{% endhint %}
