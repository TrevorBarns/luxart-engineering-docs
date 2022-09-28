---
description: Instructions on how to install LVC v3 into your server.
---

# 📄 Resource Installation

#### Download the latest stable release `Luxart.Vehicle.Control.vX.X.X.zip` (not source code) from [releases](https://github.com/TrevorBarns/luxart-vehicle-control/releases).

1.  **Copy `RageUI` folder from 'dependencies' folder in resources folder.**

    {% hint style="warning" %}
    _LVC utilizes a modified release of RageUI, please install it even if you already have another version installed._
    {% endhint %}
2.  **Copy `lvc` folder to resources folder.**

    {% hint style="warning" %}
    _Make sure your resource is named `lvc` it is required._
    {% endhint %}
3. **Add `ensure lvc` to server.cfg.**
4. **(**_**Optional**_**) Install any desired plugins from plugins folder to `lvc/PLUGINS/` (**_**see**_ [_**shared plugins**_](broken-reference)**)**

{% hint style="info" %}
This resource utilizes [globbing](https://docs.fivem.net/docs/scripting-reference/resource-manifest/resource-manifest/#globbing) which may not be supported in some linux environments. Most releases include `fxmanifest.for.Linux.Servers.no.globbing.zip` which contain a compatible fxmainfest.lua without globbing.
{% endhint %}
