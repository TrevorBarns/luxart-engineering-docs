---
description: Instructions on how to install Pro Laser 4 into your server.
---

# 📄 Resource Installation

#### Download the latest stable release `Pro.Laser.4.vX.X.X.zip` (not source code) from [releases](https://github.com/TrevorBarns/ProLaser4/releases).

1. **Copy \`ProLaser4\` to resources folder.**
2. **Add `ensure ProLaser4`to server.cfg.**

{% hint style="info" %}
This resource utilizes [globbing](https://docs.fivem.net/docs/scripting-reference/resource-manifest/resource-manifest/#globbing) which may not be supported in some linux environments. Most releases include `fxmanifest.for.Linux.Servers.no.globbing.zip` which contain a compatible fxmainfest.lua without globbing.
{% endhint %}

{% hint style="warning" %}
#### &#x20;Streamed Weapon & Weapons Meta

If you stream vintage pistol or it's associated metas in another resource, Pro Laser 4 will conflict with them. You will need to replace these or change which model Pro Laser 4 uses.
{% endhint %}

{% hint style="warning" %}
#### Streamed HUD.ytd

If you stream `hud.ytd` textures in another resource you will need to replace them or modify them if you would like to use new LIDAR weapon HUD icon or artificial reticle when in vehicles.
{% endhint %}
