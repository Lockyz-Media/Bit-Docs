---
icon: desktop-arrow-down
---

# Updating to Bit 2025.2

## Plugin Count and Plugin List functions have been moved!

With bit now exporting the pluginLoader.js file and the functions within, we've officially deprecated the old `plugin_count()` and `plugin_list()` functions from Bit: Core.



Replacement Example

```
// Old Code Example
const core = require('bit/core')

const totalPlugins = core.plugin_count()
const pluginsList = core.plugin_list()

// New Code Example
const plugins = require('bit/plugins')

const totalPlugins = plugins.count()
const pluginsList = plugins.list()
```

## New Plugin Functions

This version of Bit adds a few extra functions added to make interacting between plugins easier.

For example, the new `plugins.is_active(id)` function makes it MUCH easier to know if a plugin is installed and active.



You can find more information on these new functions in [plugins.md](functions/plugins.md "mention")

## Global "database" folder renamed to "data"

We've removed the "database" folder and replaced it with a standard "data" folder, this should be better representative of what the folder is actually for.

## Experimental: Global Exports

{% include "../../.gitbook/includes/experimental-feature.md" %}

Within bits package.json file, we've now defined a global export, under bit/plugin/\*. This means that any exported function within your plugins index.js (HAS to be named that way) can be accessed by importing "bit/plugin/PLUGINID". This should HOPEFULLY make inter-plugin compatibility MUCH better.

Example

```javascript
const xp = require('bit/plugin/bit-xp');

// Gives my user account, 10 XP and triggers the level up message if that happens
// Coming soon to a Bit: XP near YOU
xp.add_xp(835394949612175380, 10, true)
```

## Experimental: Definable Intents

{% include "../../.gitbook/includes/experimental-feature.md" %}

We've added the ability for plugins to force the bot to import required intents, before the bot defines the client. This feature should ONLY be used to define intents as it runs BEFORE bit defines the Discord Client, and other plugins.

For now, this feature is run through a second function inside your index.js file called define\_intents()

Example

```javascript
const core = require('bit/core');
const { GatewayIntentBits } = require('discord.js');

module.exports = {
    define_intents: function define_intents() {
        // Adds the MessageContent intent
        // I recommend against adding this intent unless ABSOLUTELY required
        // This intent allows the bot to see Message Content and is ABSOLUTELY dangerous
        core.add_intent(GatewayIntentBits.MessageContent)
    }
}
```

You'll also need to define some settings within your plugin.json file for this feature to work

Example

```json
{
    // ... Other Stuff
    // The below variables NEED to be set to true, and main_file MUST be accessible from within your plugin
    "has_index": true,
    "has_intents": true,
    "main_file": "index.js",
    // ... The rest of the file   
}
```

## Experimental: Definable Node Modules

{% include "../../.gitbook/includes/experimental-feature.md" %}

We've added the ability to install node modules. This will allow your plugin to install node modules from NPM that your plugin needs.

Example

```javascript
const core = require("bit/core");

module.exports = {
    start_function: function start_function() {
        // This code will install v4.0.4 of the DismonDB module
        // (You should check that out BTW, I hear a really good developer made it :])
        // https://www.npmjs.com/package/dismondb
        core.install_module('dismondb@4.0.4')
    }
}
```

