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

### Interface Guide

<figure><img src="https://lh5.googleusercontent.com/IKc4RDxnGnMk7fPz1V__YQdSN_Cb4L88x0K69px-3UFAgnv3QTRAkRyySe9L7LzuolK95gWqCzn9ifgbJbidzkj_tpXYeHNkX9JvdVcKVCPgOP97VGDMM9c8sJSpbi46LrUfA6SU0We5wbeM0A-jLzQ" alt=""><figcaption><p>Speed - Range Display / Home</p></figcaption></figure>

<figure><img src="https://lh4.googleusercontent.com/xlTeQDr_DUWn166S4Ov9nThJ0ggKg6QOBPNDZNMHWVEx-XxdYprHvbanQS8PSdvNGYWLdwUFisgEDlmDFIj1T1h5YljIXYukGJ3Z3HXugdNGGSjQbINqQ7wxyDLJCaNPxCrrsoNv859Zx4R-HuPwokI" alt=""><figcaption><p>Recalled Events / History</p></figcaption></figure>

<figure><img src="https://lh6.googleusercontent.com/PbnKGAKESHEaPK5-rB9-x7gfCNsaBXxUg-1OkQ0wv-CYRvRDlyMTNUTMhTYoRTWqiknjlbi0pH9BEuLt_lrnVuxrAfKl464ntwEoB1z5CBTDN9l6pCTucCUodUbw8uRb2fwHJo4hTyO5Af30Ku44lrI" alt=""><figcaption><p>Reticle / Sight Display</p></figcaption></figure>

### Range, Heading, and Entity Type Limitation

The lidar gun can clock AI vehicles up to your view distance (1100-1800 ft max.). Civilian vehicles clock range is limited by FiveM’s OneSync to 400-500 ft. The lidar gun can only clock targets within 20 degree heading of the gun, any larger angles results in inaccurate reading and the data is discarded. It also has no built-in entity type limitations, it can clock vehicles, bicycles, peds, animals, and aircraft, so long as its speed is greater than 0, your game can determine the speed/range of the target, and the gun and target are within 20 degree delta heading.

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

The recalled events menu can be navigated by pressing or holding `LEFT ARROW` or `RIGHT ARROW`. Holding either of these for 5 seconds will “fast-scroll” through the events. To close the recalled events menu navigate to the 1st record indicated by 1 in the top left corner and hit `LEFT ARROW` again. Recalled event data is saved every 5 minutes (if new data is present) and loaded on join.
