# 🚔 What is LVC: Fleet?

Luxart Vehicle Control: Fleet is a new separate resource based off of the innovations of [Luxart Vehicle Control v3](https://github.com/TrevorBarns/luxart-vehicle-control/). It introduces more finite control of vehicle profiles by the use of Vehicle Configuration Files, abbreviated VCFs. A vehicle configuration's settings are called **profiles** for LVC and describe all the settings encompassed in the VCF. Vehicles, by use of it's game name, are then assigned approved **profiles.**&#x20;

**LVC:F specific features over LVCv3:**

* additional profile specific settings (siren defaults, audio settings, menu permissions, etc.)
* on the fly profile selection through LVC menu
* server sided siren integration with **local override** and **peer override**

{% hint style="info" %}
**Local Override**: When active, LVC uses resident.rpf client side sirens instead of any server sided sirens.

**Peer Override:** When active, LVC uses the clients local siren selection for peers of the same _faction. See more in VCF configuration._
{% endhint %}

<figure><img src=".gitbook/assets/LVC_F Relationships.drawio.svg" alt=""><figcaption><p>LVC:F Relationship Diagram</p></figcaption></figure>

In the above diagram, you can see that LSPD, BCSO, SASP all have approved profiles 1, 2, 3. **This allows the player to select from these three profiles in the LVC:F menu**. Meanwhile, the firetruck and ambulance are assigned individual profiles and will not be able to change profiles.
