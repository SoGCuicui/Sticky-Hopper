# Sticky Hopper

> Minecraft Fabric mod allowing hoppers to be sticky!

*Based on an original idea by [Aurelien_Sama (FR)](https://www.youtube.com/watch?v=3dE8PJsWcLo&ab_channel=Aurelien_SamaAurelien_Sama), and its prototype coded by ShoukaSeikyo.*


# Features

**Sticky Hopper** — which is obviously a new block added by this mod — simply never empties completely, but retains a single item in each of its inventory slots instead.  
It has been designed to be used as a filter. Simple, small, sliceable, redstone-less filter!

**Comparators** checking for Sticky Hopper content ignore all items which are in a single copy per inventory slot.  
But as soon as there is a second item in a slot, they are counted as 2/64 (or 2/16, or whatever the maximum stack is for this type of item), not as 1/63 nor 1/64...
If there are single items in other slots, they are still ignored though.  
Non-stackable items are always ignored by Comparators as there can't be more than one in a slot, by all means.

Please note that the time to transfer a stack of items through a line of Sticky Hoppers is the same as for normal Hoppers (8 game ticks per transfer).  
But since Sticky Hoppers keep one item each, they do not actually transfer anything until the second (same) item, so they may seem slower at first.


# Craft

A Honey Bottle on top of a normal Hopper. That's it! ¯\\\_(ツ)\_/¯  
![](https://cdn.modrinth.com/data/SAqTREFl/images/59b627ded86ec63c71c7ab494a74eca903246781.png)  
Of course, it gives the empty Glass Bottle back!

It is also possible to clean up a Sticky Hopper, just place a Snowball on top of it.  
![](https://cdn.modrinth.com/data/SAqTREFl/images/5c99ddd8763d01904144c7206a6e6d920440dda2.png)  
*Didn't you know that snow cleans honey much better than a water bucket or a water bottle? The legend says that it is because the latter are not stackable!*

Please note that [a "server-side only" version exists](https://modrinth.com/mod/sticky-hopper-sso), so you can choose which one is right for you.


# Installation

As this "client / server" version adds a new block, if you want to use it on a server, clients should have it too, so they can see and craft the Sticky Hopper.

The minimum requirements are, of course the [Fabric launcher](https://fabricmc.net/use/), and the [Fabric API](https://modrinth.com/mod/fabric-api), and to copy the ".jar" file into your mods folder.  
(For default Windows installations, after running the game with the Fabric launcher at least once, just copy / paste this into the path bar of any Explorer window to open the mod folder: `%appdata%\.minecraft\mods` — and press *Enter*.)


# Miscellaneous

Performance of Sticky Hoppers is similar to that of vanilla Hoppers, if not slightly better (tested with Carpet Mod, on over 2500 idle normal and Sticky hoppers).

This mod is translated in English and French.  
You are free to use this mod in any modpacks you'd make.

This mod works without conflict with my other mod "[Speedy Hopper](https://modrinth.com/mod/speedy-hopper)", but of course you won't be able to craft a "Fast Sticky Hopper", so you'll have to make choices and design your contraptions accordingly!

I don't plan to adapt it for another modloader than Fabric.  
Please take a look at the current [issues board](https://dev.cuicui.ovh/minecraft/sticky-hopper/-/boards), and also at [the interesting ideas and suggestions](https://dev.cuicui.ovh/minecraft/sticky-hopper/-/wikis/Ideas) I've received, to see what is likely to happen sooner or later!

*Hope you'll find this mod usefull! ♥ Also, feel free to take a look at [my other mods](https://modrinth.com/user/SoGCuicui)!*


## Versions

4.0 - As the new Allay mob can be used to sort non-stackable items, this feature has been removed from this mod, so it is more vanilla-friendly again!  
3.1 - Small changes on how a Sticky Hopper filtering non-stackable items works  
3.0b - Correcting texts for Mod Menu  
3.0a - Improving the functionality of the sorting book - This is also the first release of the server-side only version!  
3.0 - Adding the ability to filter non-stackable items  
2.3 - Bugfix: Pickaxe tag added, so it's possible to mine Sticky Hoppers!  
2.2 - Cleaning craft simplified  
2.1 - Non-stackable items can finally be retained (but not filtered); Clean up craft added  
2.0 - Comparators management; Transfer cooldown bugfix  
1.0 - Initial project with operational Sticky Hoppers


## Known Incompatibilities

- _Lithium_:  
  Hoppers optimisations added in Lithium make Sticky Hoppers act like normal Hoppers!  
  I may work on this problem at some point... In the meantime, my mod disables these optimizations.
- _Vanilla Tweaks - Resource Packs_:  
  I've found two [Vanilla Tweaks resource packs](https://vanillatweaks.net/picker/resource-packs/) that have small compatibility issues, due to the change in texture of the Sticky Hoppers for this client/server version.  
  => _Directional Hoppers_ normally displays an arrow inside the hopper if it is not pointing down. It does not appear in Sticky Hoppers because of the custom texture of the honey.  
  => _3D Items_, more annoying, changes the model used for items (in the hotbar, in the hand, and also for items dropped on the ground), and unfortunately the honey texture does not appear at all.  
  Here are screenshots to illustrate those issues (without resource packs, with _Directional Hoppers_, and with _3D Items_):  
  ![](https://media.forgecdn.net/attachments/401/587/resource_pack_no.png)
  ![](https://media.forgecdn.net/attachments/401/589/resource_pack_directional_hoppers.png)
  ![](https://media.forgecdn.net/attachments/401/591/resource_pack_3d_items.png)
