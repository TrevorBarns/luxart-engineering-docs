---
description: Control trailer doors and extras while in the truck towing.
---

# 🚛 Trailer Support

## Introduction

The 'trailer-support' plugin allows more control over trailer attributes such as door position and active extras. It also adds shortcuts which can be used to toggle multiple extras across both the towing vehicle and trailer instantly.

## Configuration

1. Ensure that `plugins_installed` is set to true in `/SETTINGS.lua`.
2. Open the SETTINGS.lua located in `/PLUGINS/trailer_support`.
3. Now configure the TRAILERS table to your liking.

_Example:_ 'cfrladtcab' is the cab of a tiller fire truck, aka the tow vehicle.

{% code title="SETTINGS.lua" %}
```lua
TRAILERS = {
        ['<modelName>'] = {
                { "<shortcut name>", { { Trailer = <if the extra is on trailer or tow vehicle>, Extra = <extraId>, State = <state extra should be in when activated> }, { Trailer = < >, extra = < >, State = < > } } },
         },
	['cfrladtcab'] = { 
		{ "Raise Ladder", { { Trailer = false, Extra = 8, State = true }, { Trailer = true, Extra = 2, State = false } } },
		{ "Lower Ladder", { { Trailer = false, Extra = 8, State = false }, { Trailer = true, Extra = 2, State = true } } },
		{ "Open All Doors", { { Trailer = false, Extra = 1, State = false }, { Trailer = true, Extra = 1, State = false } } },
		{ "Close All Doors", { { Trailer = false, Extra = 1, State = true }, { Trailer = true, Extra = 1, State = true } } },
         }
}
```
{% endcode %}

#### Parameters

* **Name:** The first item in a shortcut table is the shortcut name field, this is what will show up as the name of the menu button in game. Try to limit this to a few words as it may otherwise not fit in the menu.
* **Trailer Flag:** The trailer flag is included in each shortcut sub-table and identifies if the extra ID passed is on the trailer or cab/truck.
* **Extra ID:** The extra ID intended to be toggled. This currently only allows a single extra ID, in the future it may allow for more.
* **State:** Should the extra be on or off when toggled. This ensures that regardless of the vehicle spawn state or current extra state LVC will track and toggle extras.

{% hint style="success" %}
Finished, test it out in game under the 'Plugins->Trailer Support' menu.
{% endhint %}
