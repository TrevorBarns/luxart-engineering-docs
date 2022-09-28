---
description: VCFs contain LVC:F setting for each profile. Customize them to your desire.
---

# 🛠 Customize VCFs

{% hint style="info" %}
VCF files use XML file format and must be valid for LVC:F to load them. Parsing errors will be printed to server console on resource start. You can use [xmlvalidation](https://www.xmlvalidation.com/) to check your VCF file for errors.
{% endhint %}

VCF files should be placed in `/VCF/` folder see [Assign Profiles](configure-base-settings.md#assign-profiles) on how to assign them to specific vehicles.

#### VCFROOT Attributes

```xml
<vcfroot Faction="LEO", Author="TrevorBarns">
```

{% tabs %}
{% tab title="Faction" %}
Determines if two clients profiles are compatible for peer override. __ \
__

_Example_: setting all profiles used for police departments to "LEO" would allow one agency to use peer override another agencies sirens. This is what prevents fire sirens from being overridden.
{% endtab %}

{% tab title="Author" %}
_Reserved for future implementation._
{% endtab %}
{% endtabs %}

#### :loud\_sound:HORNS/SIRENS Elements

`<HORNS>` and `<SIRENS>` are containers that can contain multiple HORN and SIREN elements respectively.

{% code title="<HORN or <SIREN " %}
```lua
Name="AIRHORN"
Option="1"
ResidentString="SIRENS_AIRHORN"
String="OISS_SSA_VEHAUD_ETC_ADAM"
Ref="OISS_SSA_VEHAUD_ETC_SOUNDSET"
Bank="DLC_SERVERSIDEAUDIO\OISS_SSA_VEHAUD_ETC"
RumblerString="OISS_SSA_VEHAUD_ETC_ADAM"
RumblerRef="OISS_SSA_VEHAUD_ETC_SOUNDSET"
RumblerBank="DLC_SERVERSIDEAUDIO\OISS_SSA_VEHAUD_ETC"
```
{% endcode %}

| Item Name      | Use                                                                                                                                                                                                                                                       |
| -------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ResidentString | GTA V tone string that references RESIDENT.rpf file.                                                                                                                                                                                                      |
| String         | Tone string that references server sided sirens. _(optional)_                                                                                                                                                                                             |
| Ref            | Tone audio bank reference for server sided sirens. _(optional)_                                                                                                                                                                                           |
| Bank           | Tone audio bank name that loaded server sided sirens bank. _(optional)_                                                                                                                                                                                   |
| RumblerString  | Tone string that references resident or server sided sirens. _(optional)_                                                                                                                                                                                 |
| RumblerRef     | Tone string that references resident or server sided sirens. _(optional)_                                                                                                                                                                                 |
| RumblerBank    | Tone audio bank name that loaded server sided sirens bank. _(optional)_                                                                                                                                                                                   |
| Option         | Determines when this tone can be played: 1-Cycle & Button, 2-Cycle Only, 3-Button Only, 4-Disabled. _(optional)_                                                                                                                                          |
| Fallback       | Determines what siren should be played when using peer override and the other player is using a siren index that is greater than the local players siren count. _e.g. playing 4th siren and the local player only has 3 sirens assigned._ _(Recommended)_ |

#### :gear: SIREN\_CONFIG Element

```xml
<SIREN_CONFIG>
	<Horn ToneID="1"/>
	<Primary_Manual ToneID="1"/>
	<Secondary_Manual ToneID="2"/>
	<Auxiliary ToneID="1"/>
	<Airhorn_Intrp Enabled="true"/>
	<Reset_Standby Enabled="true"/>
	<Park_Kill Enabled="true"/>
	<Peer_Override Enabled="false"/>
	<Local_Override Enabled="true"/>
	<Rumbler Enabled="false"/>
</SIREN_CONFIG>
```

| Item Name       | Use                                                                                                                                        |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| \*ToneID        | Which index for respective tones (HORN, PRI. MANU., SEC. MANU.)                                                                            |
| Airhorn\_Intrp  | Airhorn interrupt siren on activation, default behavior.                                                                                   |
| Reset\_Standby  | Siren resets to first index on toggle, default behavior.                                                                                   |
| Park\_Kill      | Turn siren turn off on vehicle exit, default behavior.                                                                                     |
| Local\_Override | <p>Override any server side sirens with client side sirens. <br><strong>(Must be enabled if no server sided sirens are used.)</strong></p> |
| Peer\_Override  | <p>Override other players siren choice with select profile. <br><em>(Recommend disabled if no server sided sirens are used.)</em></p>      |
| Rumbler         | <p>Enables rumbler/howler functionality <br><strong>(Requires RumblerString, RumblerRef, RumblerBank to be set.)</strong></p>              |

#### :traffic\_light: HUD Element

```xml
<HUD Enabled="true" Backlight_Mode="1"/>
```

{% tabs %}
{% tab title="Enabled" %}
Default siren controller HUD display state.&#x20;
{% endtab %}

{% tab title="Backlight Mode" %}
1 = Auto: toggle HUD backlight with headlight state

2 = Always off

3 = Always on
{% endtab %}
{% endtabs %}

#### :sound:Audio Element

```xml
<AUDIO>
	<Radio Enabled="true"/>				
	<Airhorn_SFX Enabled="false"/>
	<Manual_SFX Enabled="false"/>
	<Hazards_SFX Enabled="true"/>
	<Activity_Reminder_Interval_Index Val="1"/>
	<Scheme_Index Val="1"/>
	<SCHEMES>
		<SCHEME String="SSP2000"/>
		<SCHEME String="SSP3000"/>
		<SCHEME String="Cencom"/>
		<SCHEME String="ST300"/>
		<SCHEME String="Code3-MCB"/>
	</SCHEMES>
	<On_Volume Val="0.5"/>
	<Off_Volume Val="0.7"/>
	<Upgrade_Volume Val="0.5"/>
	<Downgrade_Volume Val="0.7"/>
	<Hazards_Volume Val="0.09"/>
	<Lock_Volume Val="0.25"/>
	<Lock_Reminder_Volume Val="0.2"/>
	<Activity_Reminder_Volume Val="0.09"/>
</AUDIO>
```

| Item Name                           | Use                                                                                                                                                                                                                               |
| ----------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Radio                               | Radio wheel functionality.                                                                                                                                                                                                        |
| \*\_SFX                             | Button sound effects. (Hazards, Airhorn, Manual tone)                                                                                                                                                                             |
| Scheme\_Index                       | Button SFX audio scheme index from `<SCHEMES>` element.                                                                                                                                                                           |
| Activity\_Reminder\_Interval\_Index | Activity reminder settings. 'Off', '1/2', '1', '2', '5', '10' in minutes.                                                                                                                                                         |
| \*\_Volume                          | SFX volume to be used.                                                                                                                                                                                                            |
| SCHEME element(s)                   | <p>Name of approved SFX folder(s) as found in <code>/UI/sounds/</code> </p><p>(See <a href="../fleet/resource-installation/advanced-configuration.md#custom-audio-schemes">Advanced Configuration - Custom Audio Schemes</a>)</p> |

#### :closed\_lock\_with\_key: Menu Element - Permissions

Each element controls the access to a menu element.

```xml
<MENU>
	<Menu_Access Enabled='true'/>
	<Menu_Main_Siren_Settings Enabled="true"/>
	<Toggle_Peer_Override Enabled="true"/>
	<Toggle_Local_Override Enabled="true"/>
	<Toggle_Airhorn_Intrp Enabled="true"/>
	<Toggle_Reset_Standby Enabled="true"/>
	<Custom_Tone_Options Enabled="true"/>
	<Custom_Manual Enabled="true"/>
	<Custom_Auxiliary Enabled="true"/>
	<Toggle_Park_Kill Enabled="true"/>
	<Menu_HUD_Settings Enabled="true"/>
	<Toggle_HUD Enabled="true"/>
	<Custom_Backlight_Mode Enabled="true"/>
	<Menu_Audio_Settings Enabled="true"/>
	<Toggle_Radio Enabled="true"/>
	<Custom_Scheme Enabled="true"/>
	<Toggle_Clicks Enabled="true"/>
	<Custom_Activity_Reminder Enabled="true"/>
	<Menu_Plugins Enabled="true"/>
</MENU>
```
