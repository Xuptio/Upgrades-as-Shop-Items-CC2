# Upgrades-as-Shop-Items-CC2
A work in progress for adding the option to buy upgrades in Carrier Command 2. 

![image](https://github.com/user-attachments/assets/2f09874e-e24a-4198-a869-6608f636d4b3)

Status 16/11/24
Storing upgrade purchases and shields in waypoints - Working well. Can store the purchase of two upgrades and the team shield count. Logic in inventory script.
Implemented awarding shields based on island difficulty, award takes place upon notification of island capture. Award is reset up dismiss of notification. 
Realizing the upgrades is proving to be a problem. For example, the scouting speed upgrade is based on the 'observation factor' in the vehicle_hud script. This, for some reason does not pull in updates to global variables and also cannot call the waypoint value storage method like the inventory, holomap, ship_log and transmissions screen can. 

For debug: 
Clicking on ship log will award two extra shields and remove all upgrades. 
Clicking on transmissions screen will reset shield count to 0.

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
The upgrade details are defined in the library_vehicle script, a unique 'upgrade_index' needs to be used for each, this is done with g_upgrade_x_counter. 

Logic that captures the player 'bought' an upgrade - Done
Logic to subtract money from player - Done, introduced new currency based on shields, awarded based on island capture and difficulty 
Logic that actions the upgrade by updating the correct values in other scripts - Done, implemented using the store values in drydock waypoint system

TODO:
Some way of saving that the player has bought the upgrade and apply it after a new session loaded - Very challenging to implement
Check if values persist through saves, game exit 


