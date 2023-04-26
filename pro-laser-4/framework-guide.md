---
description: Additional information for configuring Pro Laser 4 with frameworks.
---

# 📩 Framework Guide

### QB-Core

**Weapon**

Create a new weapon for Pro Laser 4 with attributes in \
`[qb]/qb-core/shared/weapons.lua`

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
`[qb]/qb-core/shared/items.lua`

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

TBD.
