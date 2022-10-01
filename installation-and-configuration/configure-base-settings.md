# ⚙ Configure Base Settings

## Set a Community&#x20;

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
This string should be set once, and never changed as it will result in loss of LVC saves for all players. It is not public facing so even if the server name changes it does not need to change.
{% endhint %}

## Configure Controls

#### Register Key Maps

Users may change these in their GTA V > Settings > Hotkeys > FiveM settings. \
More info: [CFX Cookbook - How RegisterKeyMappings Work](https://cookbook.fivem.net/2020/01/06/using-the-new-console-key-bindings/)\
List of Keys**:** [RegisterKeyMap Supported Keys](https://pastebin.com/u9ewvWWZ)

`open_menu_key`: sets default key for opening LVC:Fleet Menu.\
`lockout_default_key`: sets default key for toggling LVC:Fleet control lock, which disabled all controls.

****

**Indicator Controls**

These static keys cannot be changed by the end user and support controller keys as well.\
List of Keys**:** [CFX Game Reference - Controls](https://docs.fivem.net/docs/game-references/controls/)

`hazard_key`_:_ when held for __ `hazard_hold_duration` toggle 4-way flashers.\
`left_signal_key`: toggle left turn signal.\
`right_signal_key`: toggle right turn signal.

## Assign Profiles

{% code title="SETTINGS.lua" %}
```lua
---------------------VCF FILES---------------------
VCF_Files = {
	'DEFAULT.xml',		--1
	'WHELEN-295.xml',	--2
	'WHELEN-CENCOM-G.xml',	--3
	'MASTERCOM-B.xml',	--4
	'FS2000.xml',		--5
	'TMD.xml',		--6
}

VCF_Assignments = {
	['DEFAULT'] = { 1 },
	['LAPD'] = { 1, 3 }
	['<gameName>'] = { 1, 2, 3, 4, 5 }
}
```
{% endcode %}

### VCF\_Files

Table of VCF file names to be loaded on resource start. These should be locate in `/VCF/` directory. VCF Files represent profiles and contain all of LVC:Fleet's settings for that profile.

{% hint style="info" %}
To load newly installed VCF files, run `refresh` then `restart lvc_fleet`.
{% endhint %}

### VCF\_Assignements

In this table you can add additional vehicles for assignment using the vehicles `<gameName>` exactly as found in `vehicles.meta`. **It is case sensitive**.

<details>

<summary>vehicles.meta example:</summary>

```xml
...
<modelName>so2</modelName> <!-- SPAWN NAME -->
<handlingId>so2</handlingId>
<gameName>so2</gameName> <!-- GAME NAME (WHAT LVC:F USES) -->
<vehicleMakeName />
<expressionDictName>null</expressionDictName>
...
```

</details>

On the right side of the key, `{ 1, 2, 3 }`, for example, are the index's of the profiles you would like assigned to this vehicle. In the above example, that would equate to DEFAULT, WHELEN-295, WHELEN-CENCOM-G. Moreover, changing the order of the VCF\_Files, you would change which profiles are assigned.

Both R\* and LVC truncate down to 11 characters. **It is important that the first 11 characters of the vehicle game name are unique.**

* **Example**:\
  If my addon vehicles `<gameName>` is "_2008 Ford CVPI CHP_" and I have another vehicle "_2008 Ford CVPI LSPD_" both of these after truncate equate to "_2008 Ford C_" therefor LVC:Fleet will not be able to differentiate these.&#x20;

{% hint style="danger" %}
**The default or fallback key `['DEFAULT']` in the VCF\_Assignements table should always be present and never removed. Doing so will result in issues.**
{% endhint %}

#### **Wildcards**

Supported Wildcards:

* `#` represents 1 or more digits.

**How it works:**

1. LVC checks for vehicle profile matching game name. _e.g._ `['2008fpiu1']`
2. If not found, attempts wildcard search, meaning wildcards will be used _secondary_ to custom profiles. _e.g._ `['2008fpiu#']`
3. If not found, attempts a less specific wildcard search, leading and trailing numbers. _e.g._ `['#fpiu#']`
4. If not found, use default profile. _e.g._ `['DEFAULT']`

_Example_:\
\* `['veh#'] = { ... }` will be used for vehicles with game names `veh1`, `veh2`, ..., `veh9999`, etc. where exact profile not found.
