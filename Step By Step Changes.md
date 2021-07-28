src/server/zone/objects/tangible/wearables/

WearableObjectImplementation.cpp
-add code (about 50 lines) from attached file
*this will change the socket roll equation to a highly tweakable formula that includes force skills and assembly food into consideration for socket generation
*removes old non-existent variables



bin/conf/ 

config-local.lua, add the tre file
-TreFiles category (around line 149 in mtg version), add "socket_assist_tool.tre",

config.lua, add the tre file... again
-TreFiles category (around line 149 in mtg version), add "socket_assist_tool.tre",

-(also add tre file to client local harddisk)
-(also add searchTree to swgemu_live.cfg on client local harddisk)



bin/scripts/object/tangible/component/armor/

-make a copy of scale_giant_dune_kimogila.lua
-rename new file to "socket_assist_tool.lua" , no quotes
-change the four instances of scale_giant_dune_kimogila to socket_assist_tool

objects.lua
-the entries are in alphabetical order.  copy the data for scale_giant_dune_kimogila and paste where appropriate.
-replace instances of scale_giant_dune_kimogila with socket_assist_tool

serverobjects.lua
-as in objects.lua, entries are in alphabetical order.  add an includeFile entry for the socket_assist_tool.lua



bin/scripts/managers/crafting/

schematics.lua
-add a new entry {path="object/draft_schematic/armor/component/socket_assist_tool.iff"},



bin/scripts/object/tangible/loot/loot_schematic/
-copy file radar_screen_schmatic and rename it socket_assist_tool_schematic.lua
-set requiredSkill line to "crafting_droidengineer_techniques_02",
-set targetDraftSchematic line to "object/draft_schematic/armor/component/socket_assist_tool.iff",
-change four instances of radar_screen_schmatic to socket_assist_tool_schematic
-add entry to objects.lua , note alphabetical order
-add entry to serverobjects.lua , note alphabetical order
-edit the loot table to enable drop of the schematic DEV DISCRETION



bin/scripts/object/draft_schematic/armor/component

-copy deflector_shield_emitter_assembly.lua and rename it socket_assist_tool.lua
-change customObjectName to "Socket Assist Tool"
-change craftingToolTab to 32
-change complexity to 20
-change size to 2
-change xpType to "crafting_droid_general"
-change xp to ... whatever
-change assemblySkill to "droid_assembly"
-change experimentingSkill to "droid_experimentation"
-change customizationSkill to "droid_customization"
-change IngredientTemplateNames to be three entries instead of four
-change IngredientTemplateNames entries to {"craft_armor_ingredients_n", "craft_armor_ingredients_n", "craft_armor_ingredients_n"}
-change ingredientTitleNames to {"sub_assembly_frame", "plate_mounting_brackets", "power_core"}
-change ingredientSlotType from four entries to three, and to values {0, 0, 1}
-change resourceTypes to "aluminum", "copper", "object/tangible/component/armor/shared_socket_assist_tool_power_core.iff"
-change resourceQuantities to 50, 30, 1
-change contribution to three entries from four
-change target template to "object/tangible/component/armor/socket_assist_tool.iff"
-change references to deflector_shield_emitter_assembly to socket_assist_tool
-add entry to objects.lua , note alphabetical order
-add entry to serverobjects.lua , note alphabetical order


bin/scripts/object/tangible/component/armor/

-make a copy of feather_peko_albatross.lua
-rename new file to "socket_assist_tool_power_core.lua" , no quotes
-change the four instances of feather_peko_albatross to socket_assist_tool_power_core

objects.lua
-the entries are in alphabetical order.  copy the data for feather_peko_albatross and paste where appropriate
-replace instances of feather_peko_albatross to socket_assist_tool_power_core

serverobjects.lua
-as in objects.lua, entries are in alphabetical order.  add an includeFile entry for the socket_assist_tool_power_core.lua



FOR ADDING SOCKET ASSIST TOOL POWER CORE TO DROP FROM AN ALREADY EXISTING LOOT GROUP.  WHETHER THIS IS FINAL DROP METHOD IS UP FOR DEV DISCRETION
bin/scripts/loot/

items.lua, add entry
-add new entry for socket_assist_tool_power_core to make it a droppable item.  which category is most appropriate is dev's choice, though component loot sub-folder looks apt.  note alphabetical order



bin/scripts/loot/groups/creature/
-edit a loot group and add socket assist tool power core to drop
-edit a loot group and add socket assist tool schematic to drop



bin/scripts/loot/items/creature/
-copy peko albatross file and rename it to socket_assist_tool_power_core . in the file, change any instance of the peko albatross to socket_assist_tool_power_core
-edit directObjectTemplate line to point to "object/tangible/component/armor/socket_assist_tool_power_core.iff"
-take out armor special type line, armor special effectiveness line, and edit value UseCount to desired drop quantity range- this is how large of a stack of power cores can drop
-add a new line with value {"sockets",4,4,-1}
-the -1 will hide the sockets attribute from the description text, enhancing examine window aesthetic and reducing confusion among players



TEDIOUS
bin/scripts/object/draft_schematic/clothing

clothing_armor files - must be done for every armor piece to be changed

-ingredientTemplateNames, add an entry "craft_armor_ingredients_n"
-ingredientTitleNames, add an entry "socket_assist_tool"
-ingredientSlotType, add an entry, 3
-resourceTypes, add an entry "object/tangible/component/armor/shared_socket_assist_tool.iff"
-resourceQuantities, add an entry , 1
-contribution, add an entry , 100


TEDIOUS
/bin/scripts/object/tangible/wearables/armor/

armor files - must be done for every armor piece to be changed

-experimentalCombineType line, change entry (in mtg files, third entry) for sockets from 4 to 1


SIE editor

string/en
-craft_armor_ingredients_n, add entry "socket_assist_tool" , no quotes, with value "Socket Assist Tool", no quotes
-craft_armor_ingredients_n, add entry "socket_assist_tool_power_core" , no quotes, with value "Socket Assist Tool Power Core" , no quotes
-craft_armor_ingredients_n, add entry "socket_assist_tool_schematic" , no qoutes, with value "Socket Assist Tool Schematic" , no quotes
-craft_armor_ingredients_n, add entry "power_core" , no qoutes, with value "Power Core" , no quotes
-craft_armor_ingredients_d, add entry "socket_assist_tool_schematic" , no quotes, with value "A schematic for making socket assist tools that are used by armorsmiths and droid engineers when crafting armor." , no quotes
-craft_armor_ingredients_d, add entry "socket_assist_tool_power_core" , no quotes, with value "A power core used in crafting a socket assist tool.", no quotes
-craft_armor_ingredients_d, add entry "socket_assist_tool" with value "An advanced single use tool used by droid engineers and armorsmiths to reliably produce sockets when crafting armor." , no quotes

object/tangible/component/armor/
-shared_scale_giant_dune_kimogila.iff - extract location and name new file "shared_socket_assist_tool.iff", no quotes
-in the new file, change object name value to "craft_armor_ingredients_n", no quotes, and other value to "socket_assist_tool", no quotes
-in the new file, change the descriptor value to "craft_armor_ingredients_d", no quotes, and other value to "socket_assist_tool", no quotes
-in the new file, change appearance.  temporary filler: eqp_comp_jewelry_setting.apt

object/tangible/component/armor/
-shared_feather_peko_albatross.iff - extract location and name new file "shared_socket_assist_tool_power_core.iff", no quotes
-in the new file, change object name value to "craft_armor_ingredients_n", no quotes, and other value to "socket_assist_tool_power_core", no quotes
-in the new file, change the descriptor value to "craft_armor_ingredients_d", no quotes, and other value to "socket_assist_tool_power_core", no quotes
-in the new file, change appearance.  temporary filler: appearance/eqp_droid_module_s03.apt.
-in the new file, change lootAt Text to value "socket_assist_tool_power_core", no quotes.  As far as I know, this is just for completeness.

object/tangible/loot/loot_schematic/
-extract location of a file in loot schematic and rename it "shared_socket_assist_tool_schematic.iff"
-change object name to craft_armor_ingredients_n and second value to socket_assist_tool_schematic
-change detailedDescription to craft_armor_ingredients_d and second value to socket_assist_tool_schematic 
-change appearance , temporary filler: eqp_tool_handheld_viewscreen_s1.apt

object/draft_schematic/armor/component/
-extract location of a file in draft_schematic and rename it "shared_socket_assist_tool.iff"
-change appearance to same as object/tangible/component/armor appearance above (eqp_comp_jewelry_setting.apt)


CRC file

-add an entry for object/tangible/component/armor/shared_socket_assist_tool_power_core.iff
-add an entry for object/tangible/component/armor/shared_socket_assist_tool.iff
-add an entry for object/tangible/loot/loot_schematic/shared_socket_assist_tool_schematic.iff
-add an entry for object/draft_schematic/armor/component/shared_socket_assist_tool.iff
