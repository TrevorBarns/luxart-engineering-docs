---
description: Configuration of fundamental settings located in SETTINGS.lua.
---

# Configure Base Settings

### Default Settings

Configure settings to your liking. Items with prefix/postfix 'default' means the end player will be able to modify/override these later.

### Set a Community&#x20;

This unique set of characters for your community will be used for profile saving.

* The ID should be 4-6 alphanumerical characters.
* Spaces are not allowed and will not work, dashes can be used instead.
* Some examples may be your servers abbreviation, name, etc.
  * **Examples:**\
    `'LCPS'`, `'LCPSR'`, `'SARP'`, `'LSDOJ'`, `'JakesRP'`, etc.

{% hint style="info" %}
The purpose of this string is to differentiate the client side saves between servers. Since it is possible (and likely) that servers may use the same profile names, but different profile siren assignments.
{% endhint %}

{% hint style="warning" %}
This string should be set once, and never changed as it will result in loss of LVC:Fleet saves for all players. It is not public facing so even if the server name changes it does not need to change.
{% endhint %}

### Configure Controls

#### Register Key Maps

Users may change these in their GTA V > Settings > Hotkeys > FiveM settings. \
More info: [CFX Cookbook - How RegisterKeyMappings Work](https://cookbook.fivem.net/2020/01/06/using-the-new-console-key-bindings/)\
List of Keys**:** [RegisterKeyMap Supported Keys](https://pastebin.com/u9ewvWWZ)

`open_menu_key`: sets default key for opening LVC:v3 Menu.\
`lockout_default_key`: sets default key for toggling LVC:v3 control lock, which disabled all controls.



**Indicator Controls**

These static keys cannot be changed by the end user and support controller keys as well.\
List of Keys**:** [CFX Game Reference - Controls](https://docs.fivem.net/docs/game-references/controls/)

`hazard_key`_:_ when held for `hazard_hold_duration` toggle 4-way flashers.\
`left_signal_key`: toggle left turn signal.\
`right_signal_key`: toggle right turn signal.
