---
description: Toggle extras based on vehicle states.
---

# ⚡ Extra Integrations

## Introduction

The "extra\_integration" plugin handles specific actions based on vehicles state (braking, accelerating, reversing, stopped, etc.). The primary function is to enable LVC to add / remove vehicle extras based on these states. This allows vehicle developers to map extras to specific vehicle features like light bar brake lights, or rear emergency light reverse override. Future states and extras may be added later.

In addition to toggling extras, this plugin can be used to handle brake light function when stopped, automatically applying brake lights without the control needing to be held.

#### Real-life Examples:

{% embed url="https://www.youtube.com/watch?v=V-j__JXwqOk" %}
SoundOff BluePRINT Functionality
{% endembed %}

{% embed url="https://youtu.be/-Ww6jQxuL2g?t=562" %}
Whelen Cencom Carbide Functionality
{% endembed %}

### **Currently Supported States/Extras:**

|   Common Name   | String       | Trigger                                               |
| :-------------: | ------------ | ----------------------------------------------------- |
|   Brake Lights  | `Brake`      | Vehicle is in braking.                                |
|  Reverse Lights | `Reverse`    | Vehicle is in reverse.                                |
| Right Indicator | `RIndicator` | Vehicles left turn signal is active.                  |
|  Left Indicator | `LIndicator` | Vehicles right turn signal is active.                 |
|    Takedowns    | `Takedowns`  | Take-downs are enabled (requires _takedowns_ plugin). |
|   Driver Seat   | `DSeat`      | Driver seat occupied.                                 |
|   Driver Door   | `DDoor`      | Driver door not latched.                              |
|  Passenger Door | `PDoor`      | Passenger door not latched.                           |
|      Trunk      | `Trunk`      | Trunk is not latched.                                 |
|    Main Siren   | `MainSiren`  | Main/Primary siren is activated.                      |
|    Aux Siren    | `AuxSiren`   | Aux/Pwrcall siren is activated.                       |
|     Air Horn    | `AirHorn`    | Air horn is active.                                   |
|   Manual Tone   | `Manu`       | Primary or Secondary Manual tone is active.           |

### Configuration

1. Ensure that `plugins_installed` is set to true in `lvc/SETTINGS.lua`.
2. Open the SETTINGS.lua located in `/plugins/extra_integration`. Adjust settings to your liking.
3.  Now configure the EXTRA\_ASSIGNMENTS table to your liking. The Extra Assignments table is very dynamic an allows for multiple set up variations.\
    _Example:_

    {% code title="SETTINGS.lua" %}
    ```lua
    EXTRA_ASSIGNMENTS = {
        ['LAPD'] = { 
        			--[<extra_id>] = { repair = <true/false>, toggle = {<string(s)>}, reverse = <true/false>}
    			[7] = { repair = true, toggle = { "Takedowns", "AirHorn" } },
    			[8] = { repair = true, toggle = { "DSeat" } },
    			[9] = { repair = true, toggle = { "DSeat" } , reverse = true},
    		},
    }
    ```
    {% endcode %}

    ####

#### Toggle

A toggle key will toggle a single extra on trigger or multiple extra if a table is passed in.

* Single Example: `toggle = { "DSeat" }`
* Multiple Example: `toggle = { "Takedowns", "AirHorn" }`

#### Add & Remove

Add / Remove tables are not currently supported, instead use toggle. Use `reverse` flag to change when state is "active".

#### Repair Flag

A repair flag can optionally be added for higher poly extras. GTA will set extras of low poly items without repairing the vehicle, however for things like spotlights, lightbars, etc. the repair flag may need to be set. By default `repair` is set to disabled, to override add `repair = true` somewhere inside the desired trigger table.

* Examples:
  * `[7] = { repair = true, toggle = { "Takedowns", "AirHorn" } },`
  * `[8] = { repair = true, toggle = { "DSeat" } },`

{% hint style="success" %}
Finished, configure your personal settings in game under 'Plugins->Extra Integrations' menu.
{% endhint %}
