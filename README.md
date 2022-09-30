<div align="center">
  <img src="https://cdn.discordapp.com/attachments/872006424312561674/1025471851570401411/lg_s.png" alt="R1 Scripts">
  <h1>R1 Scripts</h1>
  <sub><i>Visit the store <a href="http://r1scripts.tebex.io/" title="R1 Scripts - Store">here!</a></i></sub>
</div>

## Description
Locate the hidden case, grab it and deliver it to said destination.  
The script is synchronized between all players which allows everyone to participate and to intercept the case delivery.  
Whoever that manages to deliver the case to the correct destination is rewarded.  
  
Don't worry, the script is optimized.

## Dependencies
| Script                                                                | Required |
|:----------------------------------------------------------------------|:---------|
| [QBCore](https://github.com/qbcore-framework)[^1]                     | Yes      |
| [qb-target](https://github.com/qbcore-framework/qb-target)            | Yes      |
| [qb-inventory](https://github.com/qbcore-framework/qb-inventory)[^2]  | Yes      |

[^1]: This is a framework.
[^2]: lj-inventory works as well. Similar inventories might apply, but cannot be guaranteed.

## Installation
1. Drag the folder that you downloded from keymaster to your folder of choice within your resources.  

2. Locate `qb-inventory/html/js/app.js` `Line ~570`  
  2b. Add the following segment in a proper place.
    ```lua
    } else if (itemData.name == "catchguncase") {
          $(".item-info-title").html("<p>" + itemData.label + "</p>");
          $(".item-info-description").html("<p><strong>ID: </strong><span>" + itemData.info.catchId + "</span><br /><p>" + itemData.description + "</p>");
    ```  
 
 3. Locate `qb-core/shared/items.lua`  
  3b. Add the following segment in a proper place.
    ```lua
	['catchcase'] 		= {['name'] = 'catchcase', 		['label'] = 'Case', ['weight'] = 1000, ['type'] = 'item', ['image'] = 'catchcase.png', 		['unique'] = true, ['useable'] = false, ['shouldClose'] = false, ['combinable'] = nil, ['description'] = 'Definitely not legal'},
	['catchguncase']   = {['name'] = 'catchguncase', ['label'] = 'Case', ['weight'] = 5000, ['type'] = 'item', ['image'] = 'catchguncase.png', ['unique'] = true, ['useable'] = true, 	['shouldClose'] = true,	 ['combinable'] = nil, ['description'] = 'Large Case'},
    ```  
