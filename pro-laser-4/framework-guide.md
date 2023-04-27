---
description: Additional information for configuring Pro Laser 4 with frameworks.
---

# 📩 Framework Guide

### QB-Core

**Weapon**

Create a new weapon for Pro Laser 4 with attributes in \
`qb-core/shared/weapons.lua`

{% code title="weapons.lua" %}
```lua
[`weapon_prolaser4`] = { 
    ['name'] = 'weapon_prolaser4',
    ['label'] = 'Lidar Gun',
    ['ammotype'] = 'nil',
    ['damagereason'] = 'Ticketed / Fined / Caught Speeding / Slow Down'
},
```
{% endcode %}

**Item**

Create a new item for Pro Laser 4 with attributes in \
`qb-core/shared/items.lua`

{% code title="items.lua" %}
```lua
['weapon_prolaser4'] = {
    ['name'] = 'weapon_prolaser4',
    ['label'] = 'Lidar Gun',
    ['weight'] = 1000,
    ['type'] = 'weapon',
    ['ammotype'] = 'nil',
    ['image'] = 'weapon_prolaser4.png',
    ['unique'] = true,
    ['useable'] = false,
    ['description'] = 'ProLaser4 Lidar Gun'
},
```
{% endcode %}

### Overextended

Create a new item for Pro Laser 4 with attributes in \
`ox_invetory/weapons.lua`

{% code title="weapons.lua" %}
```lua
['WEAPON_PROLASER4'] = {
	label = 'Lidar Gun',
	weight = 700,
	durability = 0.1,
},
```
{% endcode %}

### Sample Weapon Icons

<div>

<figure><img src="../.gitbook/assets/framework_icon (1).png" alt=""><figcaption><p>Small</p></figcaption></figure>

 

<figure><img src="../.gitbook/assets/framework_icon_brighter (2).png" alt=""><figcaption><p>Small Brighter</p></figcaption></figure>

 

<figure><img src="../.gitbook/assets/framework_icon_large.png" alt=""><figcaption><p>Large</p></figcaption></figure>

 

<figure><img src="../.gitbook/assets/framework_icon_large_brighter.png" alt=""><figcaption><p>Large<br>Brighter</p></figcaption></figure>

</div>
