---
icon: folder-arrow-down
---

# Updating to Bit 2025.1

## plugin.json changes

With the release of the requirements system, we've updated how to define requirements.

The requirement level is now an integer value and the key for levels has changed, you can see it below

Level 0, requires the external plugin at that specific version be loaded for your plugin to work.

Level 1, requires the external plugin to be loaded regardless of said external plugins version

Level 2, is basically a soft requirement, the external plugin is not "required" but part of your plugin will not work without it. (You should include a check for this in your code, however a feature will be added to Bit Core to aid in this in the future.)

Level 3, the plugin will NOT start if a plugin of this level is also loaded. This can be used for plugins that are incompatible with yours.



While it may never come up, please make sure that custom features check the plugins database for if your plugin is disabled.

## Configs Folder

Configs can now be added to a global configs folder in the bots root directory.

Part of Bit Plugin Certification now requires that ALL plugin configs are added to this configs folder, this is to allow the user an easy to access location that's the same for ALL plugins. Your plugins configs should also be under a folder with your plugins ID. (For example bit-cores config file is under the bit-core folder). It is HIGHLY recommended that your plugin auto-generates all configs with default values in order to allow for a user-friendly operation. A future version of Bit will include the ability to auto-generate these configs whenever the bot starts up, this wasn't included in this version to allow for the update to release sooner rather than later.

## Databases Folder

Bit now includes a databases folder, this is to allow plugin authors a dedicated place for all the files your plugin generates. This should also be used for any other files your plugin needs in order to operate, a system to automatically move these files from a folder in your plugin will come in the future.

## Banned Users Database

Bit now includes a banned-users database, while simplistic in nature, this database is used within the bots interactionCreate event to disable access to bot commands, we recommend using this database to disable access to features within your plugin to banned users. This database MUST be a manual entry to prevent issues, this means you MUST NOT create a function to add users to this database.

## Bit Core Functions

Bit Core now includes various functions for use with your plugins, in the future this will be used for querying configs and bits default databases.

These functions can be found in the [Broken link](broken-reference "mention")page.



One of these functions includes a logging function, we highly recommend using that function for logs over the standard console.log (or console.error) to allow for consistent logs across the board.

You can find more information on the logging function in [Broken link](broken-reference "mention")
