---
description: >-
  Bit 2024.2 changes very little, however we HIGHLY recommend following this
  guide to update.
icon: arrow-down-to-line
---

# Updating to Bit 2024.2

#### Use new context and installation types. <a href="#use-new-context-and-installation-types" id="use-new-context-and-installation-types"></a>

Discord.JS officially released the ability to create user-installable apps as of discord.js 14.16.0, as such we've deprecated our old method for this and have switched to the official method.

**Code to remove from commands**

Copy

```
    // Sets if the command can be used with the bot as a user-installed app or a guild-installed app.
    integration_types: {
        user: true,
        guild: true,
    },
    // Sets if the command can be used in a guild-channel, the bots DMs or a private channel (only works IF the command is user-installable, group DMs and regular user DMs)
    context_types: {
		guildChannel: true,
		botDM: true,
		privateChannel: true,
	},
```

**Code to add to commands**

(Should be in the line JUST before async execute(interaction) and include the comma)

Copy

```
.setIntegrationTypes(0,1)
.setContexts(0,1,2)
```

#### Main config moved <a href="#main-config-moved" id="main-config-moved"></a>

Bits main config file has been moved to /configs/bit/ please be sure to update your imports if you use the values in Bits default config file.
