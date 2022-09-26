---
description: Frequently asked question about LVCv3.
---

# FAQ

## Frequently Asked Questions

* [**Why is this vehicle still using the default profile even after I created a table in SIRENS\_ASSIGNMENTS?**](https://github.com/TrevorBarns/luxart-vehicle-control/wiki/FAQ#why-is-this-vehicle-still-using-the-default-profile-even-after-i-created-a-table-in-sirens\_assignments)
* [**How do I fix "SCRIPT ERROR: @lvc/UTIL/cl\_utils.lua:XX bad argument #1 to 'pairs' (table expected, got nil)"?**](https://github.com/TrevorBarns/luxart-vehicle-control/wiki/FAQ#how-do-i-fix-script-error-lvcutilcl\_utilsluaxx-bad-argument-1-to-pairs-table-expected-got-nil)

### Why is this vehicle still using the default profile even after I created a table in SIRENS\_ASSIGNMENTS?

The most likely cause for this is the use of an incorrect key in SIRENS\_ASSIGNMENTS. The key in siren assignments needs to align with the vehicles `<gameName>` as found in `vehicles.meta`. The keys first 11 characters also need to be unique due to base game limitations.

To verify this look at these two methods:

* **In game using LVC**: Enter the car in questions, navigate to 'Storage Management'. The description of the 'Save Profile' button will read "Using DEFAULT profile for "_\<gameName>_". Ensure this matches identically (case-sensitive) to the key as outlined in SIREN\_ASSIGNMENTS.
* **Out of game using `vehicles.meta`**: Locate the `vehicles.meta` file and verify that the vehicle in questions `<gameName>XXXXXXXX</gameName>` = \['XXXXXXXX'] in SIREN\_ASSIGNMENTS.

**The relevant attributes are: **_**left**_**, **_**top**_**, and **_**transform-origin**_**.**

* _left_ determines how far in percentage of the screen resolution should the HUD be placed from the left edge. If you wanted to right align the HUD you could change this to `right: XX%`, 0% being against the right edge of the display.
* _top_ determines how far down from the top the HUD should be placed.
* _transform-origin_ attribute determines which way the HUD should expand on size adjustment. For a bottom right aligned HUD you would want the transform-origin to be `right bottom`. This ensures that the HUD does not expand outside of the screen space.

### How do I fix "SCRIPT ERROR: @lvc/UTIL/cl\_utils.lua:XX bad argument #1 to 'pairs' (table expected, got nil)"?

This indicates that there was a problem loading your SIREN\_ASSIGNMENTS table from your SIRENS.lua.

What causes the table to not be loaded?

* Invalid symbol present:
  * You have accidentally made a typo and left a random symbol somewhere.
  * You pasted text from a website. Typically `RequestScriptAudioBank(“XXX”, false)`. Where the the website uses UTF8 `“` instead of ASCII `"`.
  * You have mismatched curly brackets. For every open bracket `{` there needs to be a closing bracket `}`. Too many of either will result in failure to load. Use a smart text editor like Notepad++ to highlight brackets or an online tool.
* Missing SETTINGS.lua or missing SIREN\_ASSIGNMENTS table in SIRENS.lua
