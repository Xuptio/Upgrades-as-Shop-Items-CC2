# Upgrades-as-Shop-Items-CC2
A work in progress for adding the option to buy upgrades in Carrier Command 2. ~line 1150 new code begins

![Capture](https://github.com/user-attachments/assets/6b8453ee-cf0a-40e0-b40c-523cf35fcba6)

When the player is on the inventory screen, we can write logic that captures which island type the player has clicked on. 

Island type or category_data.index == 0 is the warehouse. The idea is to add purchasable upgrades for the gameplay here. 
These could include: 
Scouting speed - observation factor = possible, has been changed in previous mods.
AWACS range - awacs effective range = possbile, other mods have implemented this
Other options will have to be investigated. 

The island category_data type and blueprints unlocked determine the 'shop' items the player can choose for that island. 
In this code I insert customer data that describes the upgrades and adds the data to the "items_unlocked" data. ~ line 1243
After this, there needs to be a flag set that the player has clicked on an upgrade as typically only the item index is passed 
to the facility which then gets the rest of the data to add to the popup display shown after selecting an item. ~ line 1339
Once the player has selected an item, if it is an upgrade we need to rewrite the item = g_item_data[g_tab_map.selected_facility_item] 
table with the upgrade data. ~ line 1495

TODO: 
Logic that captures the player 'bought' an upgrade
Logic to subtract money from player (may be some issue here, there is currently no native function for this)
Logic that actions the upgrade by updating the correct values in other scripts
Some way of saving that the player has bought the upgrade and apply it after a new session loaded


