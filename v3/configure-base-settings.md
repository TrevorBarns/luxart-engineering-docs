---
description: Configuration of fundamental settings located in SETTINGS.lua.
---

# Configure Base Settings

#### Default Settings

Configure settings to your liking. Items with prefix/postfix 'default' means the end player will be able to modify/override these later.

#### Set a Community&#x20;

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
