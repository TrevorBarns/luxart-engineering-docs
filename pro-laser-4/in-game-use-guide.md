---
description: Instructions on how to use Pro Laser 4 in game.
---

# 🎮 In Game Use Guide

### Open Lidar Display:

1. Spawn / Equip Pro Laser 4 Weapon.
2. Use `/lidar` or press `cfg.toggleMenu` control to open lidar display.

### **Controls:**

|        Key        | Description                                              |             Type             |
| :---------------: | -------------------------------------------------------- | :--------------------------: |
|        `I`        | Toggle lidar display.                                    | Modifiable in FiveM Settings |
|        `C`        | Change sniper vs. simulated sight display in 1st person. |            Static            |
|    `LEFT MOUSE`   | Clock target speed player is aimed at.                   |            Static            |
|   `RIGHT MOUSE`   | Toggle aim.                                              |            Static            |
|   `RIGHT ARROW`   | Open history and scroll next, hold to fast scroll.       |            Static            |
|    `LEFT ARROW`   | Close history and scroll previous, hold to fast scroll.  |            Static            |
|  `SCROLLWHEEL UP` | Zooms in.                                                |            Static            |
| `SCROLLWHEEL DWN` | Zooms out.                                               |            Static            |

### Commands:

`/lidar` same as `I` key, toggles lidar display.

`/lidarwipe` clears lidar history save data.

`/lidarweapon` adds Pro Laser 4 weapon to ped (vintage pistol).

**If logging is enabled & configured:**\
`/lidarrecords` opens records tablet to view previous clock data.

### Interface Guide

<figure><img src="https://lh5.googleusercontent.com/IKc4RDxnGnMk7fPz1V__YQdSN_Cb4L88x0K69px-3UFAgnv3QTRAkRyySe9L7LzuolK95gWqCzn9ifgbJbidzkj_tpXYeHNkX9JvdVcKVCPgOP97VGDMM9c8sJSpbi46LrUfA6SU0We5wbeM0A-jLzQ" alt=""><figcaption><p>Speed - Range Display / Home</p></figcaption></figure>

<figure><img src="https://lh4.googleusercontent.com/xlTeQDr_DUWn166S4Ov9nThJ0ggKg6QOBPNDZNMHWVEx-XxdYprHvbanQS8PSdvNGYWLdwUFisgEDlmDFIj1T1h5YljIXYukGJ3Z3HXugdNGGSjQbINqQ7wxyDLJCaNPxCrrsoNv859Zx4R-HuPwokI" alt=""><figcaption><p>Recalled Events / History</p></figcaption></figure>

<figure><img src="https://lh6.googleusercontent.com/PbnKGAKESHEaPK5-rB9-x7gfCNsaBXxUg-1OkQ0wv-CYRvRDlyMTNUTMhTYoRTWqiknjlbi0pH9BEuLt_lrnVuxrAfKl464ntwEoB1z5CBTDN9l6pCTucCUodUbw8uRb2fwHJo4hTyO5Af30Ku44lrI" alt=""><figcaption><p>Reticle / Sight Display</p></figcaption></figure>

### Range, Heading, and Entity Type Limitation

The lidar gun can clock AI vehicles up to your view distance (1100-1800 ft max.). Civilian vehicles clock range is limited by FiveM’s OneSync to 400-500 ft. It also has no built-in entity type limitations, it can clock vehicles, bicycles, peds, animals, and aircraft.&#x20;

**Cosine Error:** An effect when lidar gun (and therefore beam) and target are not perpendicular to each other. The larger the angle between the instrument and the target the larger the error in clocking a vehicle speed. This error results in an _underestimation_ of the vehicles speed, meaning the display will show a speed less than that of the actual target speed. While we can't actually measure the tangent or simulate the lidar beam, it is a rough estimation based on heading. The reduction also has a random scalar, to help simulate the different surfaces the beam may be hitting each with a different tangent.

It is important for players to be trained on this and understand the effects of Cosine error. The image below describes the mathematical relationship. You can read more at the link below.

<figure><img src="https://i.imgur.com/LDrXoGu.png" alt=""><figcaption><p>Credit: <a href="https://copradar.com/chapts/chapt2/ch2d1.html">copradar.com/chapts/chapt2/ch2d1.html</a></p></figcaption></figure>

<figure><img src="https://i.imgur.com/G2qleWz.png" alt=""><figcaption><p>Credit: <a href="https://copradar.com/chapts/chapt2/ch2d1.html">copradar.com/chapts/chapt2/ch2d1.html</a></p></figcaption></figure>

{% embed url="https://copradar.com/chapts/chapt2/ch2d1.html" %}

### First Person Aim Down Sight In Vehicles

While in first person, aiming down sight, and in a vehicle the rotation of the camera is limited to 80 degrees right and 178 degrees to the left. Pushing against these limits causes the screen to jitter as the resource forces your camera back into allowable angles. The camera may clip against the interior of the vehicle, this is expected and there isn’t really a solution.

### Calibration / Self-Test Behavior

If `cfg.requireCalibration` is set to true in config upon opening the lidar display or aiming down HUD sight for the first time the lidar will perform a self-test for 3 to 13 seconds. It will display a progress bar and a self-test timer. After calibration the lidar will display an empty speed-range layout.

### Recalled Events Menu

Every entity clocked will be added to the recalled events menu. If the clocked entity is the same as the last entity AND the new speed is higher than the stored speed in the recalled event table then the save data will be overridden to reflect new speed, range, and time.

<pre class="language-javascript" data-title="Update Pseudocode"><code class="lang-javascript"><strong>If (lastVeh == currVeh AND lastVehSpeed &#x3C; currVehSpeed){
</strong>    // update existing data to new speed, range, and time
}
</code></pre>

The recalled events menu can be navigated by pressing or holding `LEFT ARROW` or `RIGHT ARROW`. Holding either of these for 5 seconds will “fast-scroll” through the events. To close the recalled events menu navigate to the 1st record indicated by 1 in the top left corner and hit `LEFT ARROW` again. Recalled event data is saved every minute (if new data is present) and loaded on join.

### Records Tablet

If [persistent-records-and-tablet.md](persistent-records-and-tablet.md "mention") has been setup, then players in-game can review all players past clocks in accordance with logging settings in `config.lua`. The records tablet is a simulated tablet/laptop application that can retrieve all players previous clocks. It also allows printing clock data which includes information about the lidar gun, it's self-test state, and more.

Users clocks are submitted to the server every minute, if any are pending. All records waiting server side are inserted to the database every 5 minutes. As such, the records tablet can have a delay of up to 6 minutes.

<figure><img src="../.gitbook/assets/FiveM_b2699_GTAProcess_e2bSiHJO1X.png" alt=""><figcaption><p>Records Tablet Main Screen</p></figcaption></figure>

<figure><img src="../.gitbook/assets/FiveM_b2699_GTAProcess_AyWVo9vyVj.png" alt=""><figcaption><p>Print Preview</p></figcaption></figure>

<figure><img src="../.gitbook/assets/FiveM_b2699_GTAProcess_2m0rKuROZM.png" alt=""><figcaption><p>Print To Image</p></figcaption></figure>
