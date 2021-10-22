# Sticky Hopper

> Minecraft Fabric mod allowing hoppers to be sticky!

*Based on an original idea by [Aurelien_Sama (FR)](https://www.youtube.com/watch?v=3dE8PJsWcLo&ab_channel=Aurelien_SamaAurelien_Sama), and its prototype coded by ShoukaSeikyo.*


## Features

### Basic

**Sticky Hopper** — which is obviously a new block added by this mod — simply never empties completely, but retains a single item in each of its inventory slots instead.  
It has been designed to be used as a filter. Simple, small, sliceable, redstone-less filter!

**Comparators** checking for Sticky Hopper content ignore all items which are in a single copy per inventory slot.  
But as soon as there is a second item in a slot, they are counted as 2/64 (or 2/16, or whatever the maximum stack is for this type of item), not as 1/63 nor 1/64...
If there are single items in other slots, they are still ignored though.  
Non-stackable items are always ignored by Comparators as there can't be more than one in a slot, by all means.

Please note that the time to transfer a stack of items through a line of Sticky Hoppers is the same as for normal Hoppers (8 game ticks per transfer).  
But since Sticky Hoppers keep one item each, they do not actually transfer anything until the second (same) item, so they may seem slower at first.


### Advanced

**Since version 3.0**, for Minecraft ≥ 1.17.1, it is possible to filter non-stackable items!

Though, a single Sticky Hopper will be able to sort only one non-stackable item type, and you'll need some extra ingredients to make kind of a "recipe" inside its inventory!  
Moreover, this is a customizable option that is disabled by default!  
Indeed, the initial idea behind this Hopper is to have a vanilla-friendly behavior, and adding the ability of sorting non-stackable items is quite overkill!


#### Customization

To activate it, you have to edit the `config/sticky_hopper.toml` file.  
On a single player session, you can also use [Mod Menu](https://www.curseforge.com/minecraft/mc-mods/modmenu) to change the firsts options in-game, on-the-fly.

Here are the available options, with their default values:
- `nsif_enabled = false` - Controls if the "Non-Stackable Items Filter" is disabled (default), or enabled (`true`),
- `nsif_allow_nbts_filters = true` - By default, the NBTs (Named Binary Tags) of the incoming items are not strictly compared to those of the item in the Sticky Hopper allowing more precise filter control, turning this to `false` may have kind of side effects that you probably don't want (see **Notes** below for more details),
- `nsif_ignore_durability = false` - Turn this to `true` with `nsif_allow_nbts_filters` to allow items with different durability to "match" and be filtered,
- `nsif_ignore_enchantments = false` - Turn this to `true` with `nsif_allow_nbts_filters` to allow items with different enchantments (including no enchantments) to be considered as equals by the filter,
- `nsif_ignore_name = false` - Turn this to `true` with `nsif_allow_nbts_filters` to sort items with different names together,
- `nsif_ignore_potions = false` - Turn this to `true` with `nsif_allow_nbts_filters` (and `nsif_ignore_name`, see **Notes** below) to allow different Potions to be considered as equals,
- `nsif_observed_slot = 2` - (Editable only in the config file) - Index, starting from 0, of the slot where the item to be filtered should be placed in the Sticky Hopper inventory,
- `nsif_recipe_slots = ["minecraft:tripwire_hook", "minecraft:string", "minecraft:air", "minecraft:string", "minecraft:tripwire_hook"]` - (Editable only in the config file) - An array representing the list of ingredients in the recipe (the `nsif_observed_slot` index will be ignored, by default it is set to `minecraft:air`).

**Notes:**  
Imagine two swords strictly identical, but you used one and not the other.  
You repaired the first one so they both have the same durability (in fact, "Damage", equals 0).  
They actually will not have the same NBTs, because the "RepairCost" will be different!  
So if Sticky Hoppers are not allowing NBTs filters, these swords will not be filtered!  
But if NBTs filters are allowed, and durability not ignored, these two swords will match!  
Same remarks with Enchantments, they also increase the repair cost, so two items remain identical unless you enchant them in different ways (by merging enchantments on one item and not the other for example).  
There may be other cases — not identified here — involving the same kind of behavior, so it is certainly better to leave `nsif_allow_nbts_filters` to `true`.

Another interesting thing to mention is that short or long Potions of the same type are named the same.  
So, turning `nsif_ignore_potions` to `true` while keeping `nsif_ignore_name` to `false` will allow you to sort these Potions together.  
Turning both to `false` will allow only the exact same type of Potions to match, and both to `true` to sort all Potions together.


#### Usage

You have to configure your Sticky Hoppers by placing the item you want to filter like so (adapt this to your `nsif_recipe_slots` array):  
![](https://media.forgecdn.net/attachments/402/360/non-stackable_items_filter_recipe.png)  
Use only one Tripwire Hook and one String on both sides of your item!  
If you do so, the non-stackable item in the center will be transferred every time another identical item will take its place, at Hopper speed!

**Notes:**
- The Sticky Hopper **must** be able to insert the item into an inventory (another Hopper, a Chest, a Dropper...) to accept the transfer, a Hopper placed below will not be able to pick up anything unless the Sticky Hopper points toward it.
- New incoming Tripwire Hooks and Strings will be ignored by this Hopper.
- Enchantments of the item to be filtered are ignored. (Its durability is not ignored by default, this is customizable.)


## Craft

A Honey Bottle on top of a normal Hopper. That's it! ¯\\\_(ツ)\_/¯  
![](https://media.forgecdn.net/attachments/373/562/sticky_hopper_craft.png)  
Of course, it gives the empty Glass Bottle back!

It is also possible to clean up a Sticky Hopper, just place a Snowball on top of it.  
![](https://media.forgecdn.net/attachments/374/102/hopper_craft.png)  
*Didn't you know that snow cleans honey much better than a water bucket? The legend says that it is because the latter is not stackable!*


## Installation

This mod is for both clients and servers!  
As it adds a new block, if you want to use it on a server, clients should have it too, so they can see and craft the Sticky Hopper.

All you need is, of course, the [Fabric launcher](https://fabricmc.net/use/), the [Fabric API](https://www.curseforge.com/minecraft/mc-mods/fabric-api), and to copy the ".jar" file into your mods folder.  
(For default Windows installations, after running the game with the Fabric launcher at least once, just copy / paste this into the path bar of any Explorer window to open the mod folder: `%appdata%\.minecraft\mods` — and press *Enter*.)


## Miscellaneous

This mod is translated in English and French.  
You are free to use this mod in any modpacks you'd make.

This mod works without conflict with my other mod "[Speedy Hopper](https://www.curseforge.com/minecraft/mc-mods/speedy-hopper)", but of course you won't be able to craft a "Fast Sticky Hopper", so you'll have to make choices and design your contraptions accordingly!

I don't plan to adapt it for another modloader than Fabric.  
Please take a look at the current [issues board](https://dev.cuicui.ovh/minecraft/sticky-hopper/-/boards), and also at [the interesting ideas and suggestions](https://dev.cuicui.ovh/minecraft/sticky-hopper/-/wikis/Ideas) I've received, to see what is likely to happen sooner or later!

*Hope you'll find this mod usefull! ♥ Also, feel free to take a look at [my other mods](https://www.curseforge.com/members/cuicui_off/projects)!*


### Versions

3.0 - (≥ 1.17.1) Adding the ability to filter non-stackable items  
2.3 - (≥ 1.17) Bugfix: Pickaxe tag added, so it's possible to mine Sticky Hoppers  
2.2 - Cleaning craft simplified  
2.1 - Non-stackable items can finally be retained (but not filtered); Clean up craft added  
2.0 - Comparators management; Transfer cooldown bugfix  
1.0 - Initial project with operational Sticky Hoppers


### Known Incompatibilities

- _Lithium (≥ 1.17 only)_:
  Hoppers optimisations added in Lithium make Sticky Hoppers act like normal Hoppers!  
  I intend to work on this problem sooner or later. In the meantime, my mod the deactivation of these optimizations for Minecraft 1.17.1 (if you are using it for 1.17, just add `mixin.block.hopper=false` in "config/lithium.properties" yourself).
- _Vanilla Tweaks - Resource Packs_:
  I've found two [Vanilla Tweaks resource packs](https://vanillatweaks.net/picker/resource-packs/) that have small compatibility issues, due to the change in texture of the Sticky Hoppers.  
  => _Directional Hoppers_ normally displays an arrow inside the hopper if it is not pointing down. It does not appear in Sticky Hoppers because of the texture of the honey.  
  => _3D Items_, more annoying, changes the model used for items (in the hotbar, in the hand, and also for items dropped on the ground), and unfortunately the honey texture does not appear at all.  
  Here are screenshots to illustrate those issues (without resource packs, with _Directional Hoppers_, and with _3D Items_):  
  ![](https://media.forgecdn.net/attachments/401/587/resource_pack_no.png)
  ![](https://media.forgecdn.net/attachments/401/589/resource_pack_directional_hoppers.png)
  ![](https://media.forgecdn.net/attachments/401/591/resource_pack_3d_items.png)
