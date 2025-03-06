---
description: >-
  Bit 2024.1 changes a LOT of things, please follow this guide to get your
  plugins updated!
icon: arrow-down-to-square
---

# Updating to Bit 2024.1

As Bit 2024.1 is a major release, previous versions of the bot cannot be supported!

## plugin.json changes

All settings now use snake-case for their names!

The events and commands values have been changed to use booleans instead of strings (this is to prevent issues) and plugin versions are now required to use semantic versioning (major.minor.patch)

The bitVersion field is being removed as it will now be part of the requirements settings



| Option                     | Value Type | Default Value                                                                            | Status                                                                  |
| -------------------------- | ---------- | ---------------------------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| name                       | string     | Bit Core                                                                                 |                                                                         |
| id                         | string     | bit-core                                                                                 | NEW                                                                     |
| developer                  | string     | Lockyz Media                                                                             |                                                                         |
| version                    | string     | 2024.1.0                                                                                 | <p>CHANGED<br>- Now requires semantic versioning</p>                    |
| support                    | string     | [https://github.com/Lockyz-Media/bit/issues](https://github.com/Lockyz-Media/bit/issues) |                                                                         |
| update\_url                | string     | https://cdn.lockyzmedia.com/discord/bots/bit/plugins/core/update.json                    | <p>CHANGED<br>- Option ID is now in snake case</p>                      |
| events                     | boolean    | false                                                                                    | <p>CHANGED<br>- Now a boolean</p>                                       |
| commands                   | boolean    | true                                                                                     | <p>CHANGED<br>- Now a boolean</p>                                       |
| hasIndex                   | boolean    | true                                                                                     | NEW                                                                     |
| mainFile                   | string     | index.js                                                                                 | NEW                                                                     |
| list\_in\_plugins\_command | boolean    | true                                                                                     | NEW                                                                     |
| requirements               | array      | See Below                                                                                | <p>NEW<br><br>Requitements are not yet used bar the Bit requirement</p> |

Example plugin.json

```json
{
    "name": "Bit Core",
    "id": "bit-core",
    "developer": "Lockyz Media",
    "version": "2024.1.0",
    "support": "https://github.com/Lockyz-Media/bit/issues",
    "update_url": "https://cdn.lockyzmedia.com/discord/bots/bit/plugins/core/update.json",
    "events": true,
    "commands": true,
    "hasIndex": true,
    "mainFile": "index.js",
    "list_in_plugins_command": true,
    "requirements": {
        "bit": {
            "version": "2024.1.0",
            "level": "1"
        }
    }
}
```

## How will plugin requirements work

{% hint style="danger" %}
Plugins Requirements are being saved for another update. Please keep the only requirement as Bit.
{% endhint %}

The bot will cross reference the plugin requirements array within the plugin.json file with the bots plugin list (Currently not available). Each requirement will be listed as plugin-id:version within the Plugin List.

Plugins are required to have bit as a level 1 requirement as the requirements system is replacing the old bitVersion setting.

For Example

```json
"requirements": {
    "bit": {
        "version": "2024.1.0",
        "level": "1",
    },
    "jupiter": {
        "version": "0.2.0",
        "level": "2",
    },
    "dismon": {
        "version": "2.0.0",
        "level": "3",
    },
    "logging": {
        "version": "2.0.0",
        "level": "4",
    }
}
```

The above code will

1. Check if the current bit version is 2024.1.0
2. Fail to start if bit is not installed or the version is not 2024.1.0
3. Check if the Jupiter plugin is installed
4. Fail to start if the plugin isn't loaded, but will output to the console of the version is not the same.
5. Check if the bot has the Dismon Plugin 2.0.0
6. If Dismon is not found, the bot will instead output to the console and parts of this plugin will be disabled. If the version does not match, the bot will only output to the console.
7. Check if the logging plugin is installed
8. Fail to start if it is.

There are 3 requirement levels

Level 1, requires the external plugin at that specific version be loaded for your plugin to work.

Level 2, requires the external plugin to be loaded regardless of said external plugins version

Level 3, is basically a soft requirement, the external plugin is not "required" but part of the your plugin will not work without it. (You should include a check for this in your code)

Level 4, the plugin will NOT start if a plugin of this level is also loaded. This can be used for plugins that are incompatible with yours.

## Plugin ID's

Plugins now use an ID system to make it easier for developers wanting to use your code, to do their code. Plugin IDs will be used for plugin requirements, querying plugins (ex. loading the plugin list), and other bot functions. All plugins must use unique ID's when loaded into the bot, otherwise the bot will disable the plugin loaded second (We will only enforce plugin ID's in our certified plugins program. Plugins with the ID of bit-core will cause the bot to crash).

Plugin ID requirements are:

MUST be in Kebab Case (ex. kebab-case)!

CANNOT include numbers!

CANNOT include symbols bar the dash (-) that replaces the space!

CANNOT include a space - this WILL break the bot, use a dash (-) instead!

CANNOT use the name `bit-core`

CANNOT use offensive language.

## update.json changes

All options are now in snake case, however plugins that are made for older versions of Bit should use the legacy values. The "latest" field has been removed and all the various bit versions are under an array, if your plugin is available for legacy versions of Bit, please use the legacy values as well (We're aware this may be annoying for some, as Bit matures and we start to create a consistent code style, various things will change)

Update JSON Example

```json
{
    "download_link": "https://cdn.lockyzmedia.com/bit/plugins/xp/latest.zip",
    "bit_versions": {
        "2024.1": "2.0.0"
    }
}
```

Update JSON Example with Legacy Options - As the "developer" option was never actually used, it should NOT be used when legacy versions are available.

```json
{
    "download_link": "https://cdn.lockyzmedia.com/bit/plugins/xp/latest.zip",
    "bit_versions": {
        "2024.1": "2.0.0",
    },
    "downloadLink": "https://cdn.lockyzmedia.com/bit/plugins/xp/latest.zip",
    "latest": "2.0.0",
    "5.1": "1.0.0",
    "5.0": "1.0.0"
}
```

## New command options

Commands have been updated to include some new custom values. These new custom values allow for creating user-installable apps!

**Cooldown -** The cooldown setting sets an optional cooldown (defaults to 3 seconds) on bot commands. This setting is in seconds.

**integration\_types** - This array allows for setting when different commands CAN show up in the client, for example setting integration\_types.user to true allows the command to be seen/used when the bot is used as a user-installed app, and integration\_types.guild allows the command to be seen/used when the bot is used as a guild-installed app (the way bots have always been installed). Both options can be true.

**context\_types** - This array allows for setting where a command can show up in the client. For example, context\_types.guild\_channel allows the command to be seen in guild channels, context\_types.bot\_dm allows the command to be seen in the bots DM's and context\_types.private\_channel allows the command to be used in the users private DM's (with other people) and group DMs. However context\_types.private\_channel only works if the integration\_types.user is on.



| Option                          | Value Type | Default Value |
| ------------------------------- | ---------- | ------------- |
| cooldown                        | integer    | 5             |
| integration\_types.user         | boolean    | true          |
| integration\_types.guild        | boolean    | true          |
| context\_types.guild\_channel   | boolean    | true          |
| context\_types.bot\_dm          | boolean    | true          |
| context\_types.private\_channel | boolean    | true          |

Format

```javascript
// Cooldowns can be any number upto the 32-bit integer limit. This number is in seconds!
cooldowns: 5,

integration_types: {
    user: true,
    guild: true,
},

context_types: {
    guild_channel: true,
    bot_dm: true,
    private_channel: true,
},
```

## Run code on bot startup

Bit now allows plugins to run code on startup!

This means that within your plugin.json file you can tell the bot to run the code within the mainFile file!



The starting function MUST be called `startFunction` the casing of the function name MAY change in the future to increase consistency within Bit.

Example - index.js from Bit: Core

```javascript
module.exports = {
    startFunction: function startFunction() {
        console.log("Bit: Core Successfully Loaded!")
    }
};
```
