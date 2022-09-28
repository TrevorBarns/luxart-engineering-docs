---
description: >-
  Plugins add additional functionality to the base resources for LVC:F and
  LVCv3.
---

# 🔌 Introduction to Plugins

Plugins are an easy way to add additional functionality Luxart Vehicle Control. Plugins provide the necessary files to run seamlessly with the base resource. The functionality provided in plugins can easily be integrated with the menu if you so decide, but by default are placed in a "Plugins" submenu.

### Current Available Plugins

{% content-ref url="take-downs.md" %}
[take-downs.md](take-downs.md)
{% endcontent-ref %}

{% content-ref url="extra-controls.md" %}
[extra-controls.md](extra-controls.md)
{% endcontent-ref %}

{% content-ref url="extra-integrations.md" %}
[extra-integrations.md](extra-integrations.md)
{% endcontent-ref %}

{% content-ref url="traffic-advisor.md" %}
[traffic-advisor.md](traffic-advisor.md)
{% endcontent-ref %}

{% content-ref url="trailer-support.md" %}
[trailer-support.md](trailer-support.md)
{% endcontent-ref %}

### Installation

1. Enable plugin support by setting `plugins_installed` to true located in `lvc/SETTINGS.lua`.
2. Copy the desired plugin folder from the release .zip to the PLUGINS folder.
3. Configure the desired plugin to your liking using `/PLUGINS/XXXXX/SETTINGS.lua`. More information can be found on the desired plugins wiki page.

\
