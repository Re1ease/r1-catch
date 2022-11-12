<div align="center">
  <img src="https://cdn.discordapp.com/attachments/872006424312561674/1025471851570401411/lg_s.png" alt="R1 Scripts">
  <h1>R1 Scripts</h1>
  <sub><i>Visit the store <a href="http://r1scripts.tebex.io/" title="R1 Scripts - Store">here!</a></i></sub>
</div>

## Description
Locate the hidden case, grab it and deliver it to said destination.  
The script is synchronized between all players which allows everyone to participate and to intercept the case delivery.  
Not only are the events synced, but so are the props.  
Whoever that manages to deliver the case to the correct destination is rewarded.  
  
Don't worry, the script is optimized as shown in the showcase video.

Need help? Hop into the [Discord](https://discord.gg/GB9YEXeP5k).

## Showcase
[Video Showcase](https://www.youtube.com/watch?v=_Ivuig2SzrY)

## Dependencies
| Script                                                                | Required |
|:----------------------------------------------------------------------|:---------|
| [QBCore](https://github.com/qbcore-framework)[^1]                     | Yes      |
| [qb-target](https://github.com/qbcore-framework/qb-target)            | Yes      |
| [qb-inventory](https://github.com/qbcore-framework/qb-inventory)[^2]  | Yes      |
| [PolyZone](https://github.com/mkafrin/PolyZone)  			| Yes      | 

[^1]: This is a framework.
[^2]: lj-inventory works as well. Similar inventories might apply, but cannot be guaranteed.

## Config
<details>
  <summary>Click to display</summary> 
	
   ```lua
    Config = {}

------------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------------
--GENERAL---------------------------------------------------------------------------------------------

-- Name of the item. Has to match an item-name from qb-core/shared/items.lua.
Config.Item = "catchcase"

-- The object that the player should look for/carry.
Config.Object = "hei_prop_heist_thermite_case"

-- The ped that recieves the delivery.
Config.Ped = "s_m_y_blackops_02"

-- In-game command to start the event.
Config.Command = {
	command = "startcatchevent",
	description = "Admin Command",
	permission = "admin"
}

-- Sets where the object is attached to the ped.
Config.AttachObject = {
	bone = 57005,
	xPos = 0.30, yPos = 0, zPos = -0.01,
	xRot = 90.0, yRot = 90.0, zRot = -60.0
}

------------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------------
--REWARDS---------------------------------------------------------------------------------------------

-- If true; Uses the below config with an item that opens a secondary inventory. If false; You set the reward system through server/rewards.lua.
Config.UseDefaultRewardSystem = true

-- Name of the item that the player recieves upon delivery.
Config.RewardItem = "catchguncase"

-- The amount of slots that the secondary inventory should have. Should reflect the amount of rewards that you are giving from below.
Config.RewardInventorySlots = 5

-- How much the secondary inventory should weigh, in milligrams.
Config.RewardInventoryWeight = 100000

-- Contents of Config.RewardItem.
Config.RewardItems = {
	"weapon_revolver",
	"weapon_pistol50",
	"weapon_microsmg",
	"weapon_minismg",
	"pistol_ammo"
}

-- If true; Takes random items from Config.RewardItems. If false, gives all of them.
Config.RewardIsRandom = true

-- If Config.RewardIsRandom is true; The amount of random items that are given.
Config.RewardRandomCount = 3

------------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------------
--BLIPS-----------------------------------------------------------------------------------------------

-- The area that the players has to search to find the object.
Config.SearchingArea = {
	offset = 80, 	-- Randomizes the x & y to not center the location, thus increasing difficulty.
	radius = 100.0,	-- How big is the radius of the circle?
	sprite = 9,
	color = 6,
	alpha = 200
}

-- The blip that appears once the object has been picked up. Follows the carrier.
Config.Tracker = {
	sprite = 119,
	color = 6,
	scale = 1.3,
	text = "Mysterious Case",

	trackerUpdate = 8000 	-- How often the blip should update its position in ms.
}

-- The spot where the delivery location is.
Config.DeliverSpot = {
	sprite = 514,
	color = 0,
	scale = 1.3,
	text = "Delivery Spot"
}

------------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------------
--POLY------------------------------------------------------------------------------------------------

-- Surrounds the object whilst being on the ground in the initial stage.
Config.PolyObject = {
	label = "Pickup",
	icon = "fas fa-box",
	distance = 2.0,
	debug = false
}

-- Surrounds the ped that is to recieve the delivery.
Config.PolyPed = {
	label = "Deliver Case",
	icon = "fas fa-hand-holding-heart",
	distance = 1.5,
	debug = false
}

------------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------------
--EMAIL-----------------------------------------------------------------------------------------------

-- Sends a different email to the police, or the jobs that you list.
Config.PoliceJobs = {"police", "sheriff"}

-- The email that is sent to the jobs that you list above.
Config.EmailPolice = {
	sender = "Dispatch",
	subject = "Suspicious Case",
	message = "Chatter about a suspicious case is floating on the dark forums.<br/>The case is green and contains biohazardous material. Be on the look out!"
}

-- The email that is sent to everyone else.
Config.EmailGeneral = {
	sender = "Anonymous",
	subject = "Job Offer",
	message = "I need you to retrieve my case, and I will give you a hefty payout for the trouble. Do whatever you have to do to locate and deliver the case to me. I marked a rough location on your map where the package was seen last. Do your part, solider."
}

------------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------------
--LOCATIONS-------------------------------------------------------------------------------------------

-- Coordinates where the object randomly spawns.
Config.Locations = {
	-- Paleto
	vector3(-837.93, 5394.22, 34.62),
    vector3(-535.85, 5293.05, 74.17),
    vector3(-69.63, 6255.76, 31.09),
    vector3(162.22, 6655.72, 31.57),

    -- Sandy Shores
    vector3(1872.7, 3750.4, 33.0),
    vector3(2396.53, 4297.76, 32.56),
    vector3(913.11, 3651.5, 36.12),
    vector3(375.54, 3574.44, 33.29),

    -- Grapeseed
    vector3(2565.63, 4658.59, 34.05),
    vector3(2317.1, 4857.03, 41.81),
    vector3(1726.96, 4784.27, 41.98),
    vector3(2380.73, 5029.66, 45.95),

    -- City/Mirror Park
    vector3(1121.44, -643.9, 56.81),
    vector3(1172.64, -390.05, 71.58),
    vector3(1083.17, -788.28, 58.26),
    vector3(1390.36, -789.13, 67.43),

    -- City/Vinewood
    vector3(236.63, 132.74, 102.6),
    vector3(381.71, 356.99, 102.57),
    vector3(-134.58, 214.91, 94.81),
    vector3(-428.25, 290.16, 83.23)
}

-- Coordinates where the ped that recieves the delivery randomly spawns.
Config.DropOff = {
	vector4(-667.73, 5724.52, 24.47, 75.34),
	vector4(-2166.13, 5197.03, 16.88, 98.6),
	vector4(-2792.39, 1440.97, 100.93, 182.17),
	vector4(-3064.6, 619.62, 7.38, 110.45),
	vector4(-2008.19, -314.87, 32.1, 55.45),
	vector4(-1714.53, -199.0, 57.69, 224.68),
	vector4(2695.48, 866.12, 80.97, 273.24),
	vector4(2471.33, 1594.95, 32.72, 92.24),
	vector4(2178.26, 3497.44, 45.37, 38.15),
	vector4(3817.4, 4441.9, 2.81, 276.19),
	vector4(-1708.3, 5323.66, 5.89, 259.8),
	vector4(-1502.89, 1521.08, 115.29, 352.4),
	vector4(-1423.59, -215.43, 46.5, 185.26),
	vector4(-1803.7, -1197.96, 13.02, 235.6),
}
   ```
</details> 

## Installation
1. Drag the folder that you downloded from keymaster to your folder of choice within your resources.  
---
2. Locate `qb-inventory/html/js/app.js` `Line ~570`  
  2b. Add the following segment in a proper place.
    ```js
    } else if (itemData.name == "catchguncase") {
          $(".item-info-title").html("<p>" + itemData.label + "</p>");
          $(".item-info-description").html("<p><strong>ID: </strong><span>" + itemData.info.catchId + "</span><br /><p>" + itemData.description + "</p>");
    ```  
---
3. Locate `qb-core/shared/items.lua`  
   3b. Add the following segment in a proper place.
    ```lua
	['catchcase'] 		= {['name'] = 'catchcase', 		['label'] = 'Case', ['weight'] = 1000, ['type'] = 'item', ['image'] = 'catchcase.png', 		['unique'] = true, ['useable'] = false, ['shouldClose'] = false, ['combinable'] = nil, ['description'] = 'Definitely not legal'},
	['catchguncase']   = {['name'] = 'catchguncase', ['label'] = 'Case', ['weight'] = 5000, ['type'] = 'item', ['image'] = 'catchguncase.png', ['unique'] = true, ['useable'] = true, 	['shouldClose'] = true,	 ['combinable'] = nil, ['description'] = 'Large Case'},
    ```  
