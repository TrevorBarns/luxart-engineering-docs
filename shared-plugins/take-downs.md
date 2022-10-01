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

    |            Variable Name           | Action                                                                                                                               | Data Constraints |          Common Name          | Default |
    | :--------------------------------: | ------------------------------------------------------------------------------------------------------------------------------------ | ---------------- | :---------------------------: | :-----: |
    |         `tkd_masterswitch`         | Toggles if plugin is enabled. Disabling this removes it from plugin menu, stops it's functionality.                                  | true / false     |         Master-switch         |   true  |
    |              `tkd_key`             | Key that activates take-downs, if tkd\_combokey is depressed or disabled.                                                            | Static Control # |              Key              |    74   |
    |           `tkd_combokey`           | Activates tkd\_key when depressed if not set to 0.                                                                                   | Static Control # |            Combokey           |    21   |
    |       `tkd_intensity_default`      | Sets default brightness of take-down light                                                                                           | 0-150            |       Default Intensity       |   100   |
    |        `tkd_radius_default`        | Sets default spread angle in reference to vehicle.                                                                                   | 0-90             |         Default Radius        |    50   |
    |       `tkd_distance_default`       | Sets default max distance light is visible, brightness effected by fall-off at distance.                                             | 0-250            |        Default Distance       |    50   |
    |        `tkd_falloff_default`       | Sets default distance that the light begins to dim due to distance.                                                                  | 0-2000           |        Default Falloff        |   1000  |
    |          `tkd_sync_radius`         | Distance at which take-downs are synced to other users. ⚠️ This has extreme implications on performance, 400 or less is recommended. | 0-10500          |          Sync Radius          |   400   |
    | `tkd_highbeam_integration_default` | Sets default state for high-beam integration.                                                                                        | 1-3              | Default High-Beam Integration |    2    |

{% hint style="success" %}
Finished, configure your personal settings in game under in-game 'Plugins->Takedowns' menu.
{% endhint %}
