---
description: >-
  Light up the area in front of your patrol vehicle at the press of a button or
  by using high-beams.
---

# 🔦 Take-downs

### Introduction

LVCs first plugin, "takedowns" moves previously implemented take down features to this plugin. The take downs plugin allows clients to activate a bright light in front of their vehicle at the push of a button. The use is to imitate real life take-downs, which are used for illuminating traffic stops and increasing visibility in the dark when attempting to locate persons or things.

It works by using CFX native [DrawSpotlight(...)](https://runtime.fivem.net/doc/natives/?\_0xD0F64B265C8C8B33). It does not, modify any extras, but can integrate with your vehicles high-beam system to either trigger on high-beams or trigger high-beams on take-down activation.

### Configuration

1. Ensure that `plugins_installed` is set to true in `/SETTINGS.lua`.
2.  Open the SETTINGS.lua located in `/PLUGINS/takedowns`. Adjust settings to your liking.

    <table><thead><tr><th width="285">Variable Name</th><th width="296">Action</th><th align="center">Data Constraints</th><th data-hidden align="center">Common Name</th><th data-hidden align="center">Default</th></tr></thead><tbody><tr><td><code>tkd_masterswitch</code></td><td>Toggles if plugin is enabled. Disabling this removes it from plugin menu, stops it's functionality.</td><td align="center">true / false</td><td align="center">Master-switch</td><td align="center">true</td></tr><tr><td><code>tkd_key</code></td><td>Key that activates take-downs, if tkd_combokey is depressed or disabled.</td><td align="center">Static Control #</td><td align="center">Key</td><td align="center">74</td></tr><tr><td><code>tkd_combokey</code></td><td>Activates tkd_key when depressed if not set to 0.</td><td align="center">Static Control #</td><td align="center">Combokey</td><td align="center">21</td></tr><tr><td><code>tkd_intensity_default</code></td><td>Sets default brightness of take-down light</td><td align="center">0-150</td><td align="center">Default Intensity</td><td align="center">100</td></tr><tr><td><code>tkd_radius_default</code></td><td>Sets default spread angle in reference to vehicle.</td><td align="center">0-90</td><td align="center">Default Radius</td><td align="center">50</td></tr><tr><td><code>tkd_distance_default</code></td><td>Sets default max distance light is visible, brightness effected by fall-off at distance.</td><td align="center">0-250</td><td align="center">Default Distance</td><td align="center">50</td></tr><tr><td><code>tkd_falloff_default</code></td><td>Sets default distance that the light begins to dim due to distance.</td><td align="center">0-2000</td><td align="center">Default Falloff</td><td align="center">1000</td></tr><tr><td><code>tkd_sync_radius</code></td><td>Distance at which take-downs are synced to other users. ⚠️ This has extreme implications on performance, 400 or less is recommended.</td><td align="center">0-10500</td><td align="center">Sync Radius</td><td align="center">400</td></tr><tr><td><code>tkd_highbeam_integration_default</code></td><td>Sets default state for high-beam integration.</td><td align="center">1-3</td><td align="center">Default High-Beam Integration</td><td align="center">2</td></tr></tbody></table>

{% hint style="success" %}
Finished, configure your personal settings in game under in-game 'Plugins->Takedowns' menu.
{% endhint %}
