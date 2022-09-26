---
description: Stream custom sirens from the server to
---

# Server Sided Siren Integration

### Introduction

Below are two third-party resources that allow for streaming of R\* audio files from server to client. These audio files can be for various things but some people use them for sirens.

* **Server-Sided-Sounds-and-Sirens (SAS)**\
  Supports up to 214 tones for FREE. I am in no way affiliated with this resource or its creator.&#x20;

{% embed url="https://github.com/fk-1997/Server-Sided-Sounds-and-Sirens" %}
Server Sided Sounds and Sirens Github
{% endembed %}

* **WM-ServerSirens (WM-SS)**\
  Provides 8 tones for free, but for more there is a paywall. I am in no way affiliated with 'Walshey Modifications' or this resource.

{% embed url="https://forum.cfx.re/t/release-wm-serversirens-fivem-server-side-siren-resource-walshey-marcus/1491908" %}
WM-ServerSirens Release Page CFX
{% endembed %}

***

### How to Integrate:

### 1. Request Audio Bank:

First we need to request the audio bank, this loads the audio for the client prior to use. We can place these lines anywhere in SIRENS.lua.

{% hint style="warning" %}
&#x20;Currently only 7 audio banks are supported. We are not sure why, seems like a FiveM lua **** limitation.
{% endhint %}

**Server-Sided-Sounds-and-Sirens:**\
Below are the audio banks supported by SAS. **You only need to request audio banks you intend to use.** All audio banks below support 6 tones each, besides the last one, OISS\_SSA\_VEHAUD\_ETC, which supports 16 tones.

```lua
RequestScriptAudioBank("DLC_SERVERSIDEAUDIO\\OISS_SSA_VEHAUD_LSPD_NEW", false)
RequestScriptAudioBank("DLC_SERVERSIDEAUDIO\\OISS_SSA_VEHAUD_LSPD_OLD", false)
RequestScriptAudioBank("DLC_SERVERSIDEAUDIO\\OISS_SSA_VEHAUD_LSSD_NEW", false)
RequestScriptAudioBank("DLC_SERVERSIDEAUDIO\\OISS_SSA_VEHAUD_LSSD_OLD", false)
RequestScriptAudioBank("DLC_SERVERSIDEAUDIO\\OISS_SSA_VEHAUD_BCSO_NEW", false)
RequestScriptAudioBank("DLC_SERVERSIDEAUDIO\\OISS_SSA_VEHAUD_BCSO_OLD", false)
RequestScriptAudioBank("DLC_SERVERSIDEAUDIO\\OISS_SSA_VEHAUD_SAHP_NEW", false)
RequestScriptAudioBank("DLC_SERVERSIDEAUDIO\\OISS_SSA_VEHAUD_SAHP_OLD", false)
RequestScriptAudioBank("DLC_SERVERSIDEAUDIO\\OISS_SSA_VEHAUD_SAHP_BIKE", false)
RequestScriptAudioBank("DLC_SERVERSIDEAUDIO\\OISS_SSA_VEHAUD_NOOSE_NEW", false)
RequestScriptAudioBank("DLC_SERVERSIDEAUDIO\\OISS_SSA_VEHAUD_NOOSE_OLD", false)
RequestScriptAudioBank("DLC_SERVERSIDEAUDIO\\OISS_SSA_VEHAUD_FIB_NEW", false)
RequestScriptAudioBank("DLC_SERVERSIDEAUDIO\\OISS_SSA_VEHAUD_FIB_OLD", false)
RequestScriptAudioBank("DLC_SERVERSIDEAUDIO\\OISS_SSA_VEHAUD_RHPD_NEW", false)
RequestScriptAudioBank("DLC_SERVERSIDEAUDIO\\OISS_SSA_VEHAUD_RHPD_OLD", false)
RequestScriptAudioBank("DLC_SERVERSIDEAUDIO\\OISS_SSA_VEHAUD_DPPD_NEW", false)
RequestScriptAudioBank("DLC_SERVERSIDEAUDIO\\OISS_SSA_VEHAUD_DPPD_OLD", false)
RequestScriptAudioBank("DLC_SERVERSIDEAUDIO\\OISS_SSA_VEHAUD_LSIA_NEW", false)
RequestScriptAudioBank("DLC_SERVERSIDEAUDIO\\OISS_SSA_VEHAUD_LSIA_OLD", false)
RequestScriptAudioBank("DLC_SERVERSIDEAUDIO\\OISS_SSA_VEHAUD_LSPP_NEW", false)
RequestScriptAudioBank("DLC_SERVERSIDEAUDIO\\OISS_SSA_VEHAUD_LSPP_OLD", false)
RequestScriptAudioBank("DLC_SERVERSIDEAUDIO\\OISS_SSA_VEHAUD_LSFD_NEW", false)
RequestScriptAudioBank("DLC_SERVERSIDEAUDIO\\OISS_SSA_VEHAUD_LSFD_OLD", false)
RequestScriptAudioBank("DLC_SERVERSIDEAUDIO\\OISS_SSA_VEHAUD_LSCOFD_NEW", false)
RequestScriptAudioBank("DLC_SERVERSIDEAUDIO\\OISS_SSA_VEHAUD_LSCOFD_OLD", false)
RequestScriptAudioBank("DLC_SERVERSIDEAUDIO\\OISS_SSA_VEHAUD_BCFD_NEW", false)
RequestScriptAudioBank("DLC_SERVERSIDEAUDIO\\OISS_SSA_VEHAUD_BCFD_OLD", false)
RequestScriptAudioBank("DLC_SERVERSIDEAUDIO\\OISS_SSA_VEHAUD_SANFIRE_NEW", false)
RequestScriptAudioBank("DLC_SERVERSIDEAUDIO\\OISS_SSA_VEHAUD_SANFIRE_OLD", false)
RequestScriptAudioBank("DLC_SERVERSIDEAUDIO\\OISS_SSA_VEHAUD_SAMS_NEW", false)
RequestScriptAudioBank("DLC_SERVERSIDEAUDIO\\OISS_SSA_VEHAUD_SAMS_OLD", false)
RequestScriptAudioBank("DLC_SERVERSIDEAUDIO\\OISS_SSA_VEHAUD_USFS_NEW", false)
RequestScriptAudioBank("DLC_SERVERSIDEAUDIO\\OISS_SSA_VEHAUD_USFS_OLD", false)
RequestScriptAudioBank("DLC_SERVERSIDEAUDIO\\OISS_SSA_VEHAUD_ETC", false)
```

**WM-ServerSirens**:

*   Free:

    ```lua
    RequestScriptAudioBank("DLC_WMSIRENS\\SIRENPACK_ONE", false)
    ```
*   Paid:

    ```lua
    RequestScriptAudioBank("DLC_WALSHEY\\SIRENPACK_ONE", false)
    RequestScriptAudioBank("DLC_WALSHEY\\SIRENPACK_TWO", false)
    RequestScriptAudioBank("DLC_WALSHEY\\SIRENPACK_THREE", false)
    RequestScriptAudioBank("DLC_WALSHEY\\SIRENPACK_FOUR", false)
    ```

_Example:_

<figure><img src="https://camo.githubusercontent.com/54fbf1ef00b524db8ed9b5c32ec8e124e98024eafa9a4a08732977bf30a2e1ef/68747470733a2f2f692e6779617a6f2e636f6d2f62303231343339363132346665366134663866343865396238316665343830342e706e67" alt=""><figcaption><p>SIRENS.lua</p></figcaption></figure>

{% hint style="warning" %}
Make sure you are using ASCII quotes not UTF8 quotes from CFX forum post. Correct: " vs Incorrect: “. This will result in a parsing error and many other errors as SIRENS.lua file will not be loaded.
{% endhint %}

### 2. Configuration of SIRENS table (SIRENS.lua)

Now that we have told GTA V to load the requested audio banks from Step 1, we now need to create the specific tones.

* To add additional tones copy & paste additional lines into the SIRENS table.
  * Take note of the incrementing numbers, they are the siren IDs and we will need them to assign sirens later. These are not generated so you may have to manually renumber lines.
  * You can change the name to your desired siren name such as 'Wail', 'Yelp', '295-Wail', 'FSS-Rumbler'. See: [Setup & Configuration - Wiki](https://github.com/TrevorBarns/luxart-vehicle-control/wiki/Setup-&-Configuration#configuration-of-sirens-table-sirenslua) for more information.
* To replace tones change the **`String`** to the desired siren string `SIREN_XXXX` or `OISS_SSA_XXXX` and the **`Ref`** to `DLC_WMSIRENS_SOUNDSET` or `OISS_SSA_VEHAUD_XXXX`.\
  ⚠️ _This is not recommended. Instead, consider managing the use of default tones by removing them from SIREN\_ASSIGNEMENTS if so desired._

### Troubleshooting

First, to determine if it is a LVC or AWC issue use the Server Side Audio Tester, follow readme on configuration.

* If it works in SSAT then it is an LVC configuration error, verify your audio banks, strings, and refs for typos.
* If it does not work in SSAT, it is likely your AWC is corrupt, too large, or has a tone that is too large. Try "balancing" tone sizes across multiple AWCs use empty wav files to fill empty tone slots.

{% embed url="https://github.com/TrevorBarns/Server-Side-Audio-Tester" %}
Server Side Audio Tester Github
{% endembed %}

\
