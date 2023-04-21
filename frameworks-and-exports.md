---
description: Supported frameworks and exports.
---

# ➕ Frameworks & Exports

### Frameworks

The below frameworks are supported, please report any conflicts by creating an issue on the respective product or on [my discord](https://discord.link/lvc).

{% hint style="success" %}
QBCore: so long as you do not have have [qb-extras](https://github.com/MrEvilGamer/qb-extras/) installed.
{% endhint %}

{% hint style="success" %}
ESX
{% endhint %}

### Exports&#x20;

**Vehicle State Change Event** (_Coming v3.2.10)_\
Broadcasts event when LVC vehicle state changes. Returns a table/array of data below:\


<table data-view="cards"><thead><tr><th>Table Index/Key</th><th>Description</th><th>Options</th></tr></thead><tbody><tr><td><code>state_indic</code></td><td>Indicator/turn-signal state.</td><td><p><code>0</code>: off</p><p><code>1</code>: left on</p><p><code>2</code>: right on,</p><p><code>3</code>: hazard/4-ways on</p></td></tr><tr><td><code>actv_manu</code></td><td>Is manual siren on?</td><td><code>true</code>, <code>false</code></td></tr><tr><td><code>actv_horn</code></td><td>Is the horn on?</td><td><code>true</code>, <code>false</code></td></tr><tr><td><code>state_lxsiren</code></td><td>Main siren tone ID.</td><td><p><code>0</code>: off,</p><p><code>>0</code>: tone ID of main siren </p></td></tr><tr><td><code>state_pwrcall</code></td><td>Powercall/auxiliary siren tone ID.</td><td><p><code>0</code>: off</p><p><code>>0</code>: tone ID of aux/powercall </p></td></tr><tr><td><code>state_airmanu</code></td><td>Airhorn/manual siren tone ID.</td><td><p><code>0</code>: off</p><p><code>>0</code>: tone ID of AirManu</p></td></tr></tbody></table>

{% code title="Example Event Handler" %}
```lua
RegisterNetEvent('lvc:UpdateThirdParty')
AddEventHandler('lvc:UpdateThirdParty', function(update_data)
    local siren_tone = update_data['state_lxsiren'] 
    if siren_tone > 0 then
        --Sirens on, do something...
    end
end)
```
{% endcode %}
