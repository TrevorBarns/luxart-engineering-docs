---
description: Instructions on how to install LVC:F into your server
---

# 📄 Resource Installation

Download the latest stable release `Luxart.Vehicle.Control.Fleet.vX.X.X.zip` (not source code) from [releases](https://github.com/TrevorBarns/luxart-vehicle-control-fleet/releases).

1. Copy `RageUI` folder from 'dependencies' folder in resources folder.
2. Copy `lvc_fleet` folder to resources folder.
3. Add `ensure lvc_fleet` to server.cfg.

{% hint style="warning" %}
Make sure your resource is named `lvc` it is required.
{% endhint %}

{% hint style="warning" %}
LVC utilizes a modified release of RageUI, please install it even if you already have an older version. This release should be backwards compatible, please report any issues and I can resolve them for you.
{% endhint %}

{% hint style="info" %}
This resource utilizes [globbing](https://docs.fivem.net/docs/scripting-reference/resource-manifest/resource-manifest/#globbing) which may not be supported in some linux environments. Most releases include `fxmanifest.for.Linux.Servers.no.globbing.zip` which contain a compatible fxmainfest.lua without globbing.
{% endhint %}
