---
icon: dev
---

# Definable Intents

{% include "../../.gitbook/includes/experimental-feature.md" %}

Added in Bit 2025.2, you can now define intents to be added to the bot before the bot starts.



This feature adds a new function that runs when the bot first starts `define_intents()` runs BEFORE the Discord client is defined and started, meaning that any discord.js specific functions DO NOT work.

This function can be used to run literally any code, however plugins will NOT be certified if they run any code within this function that isn't used to define an intent, or a node module.



Within your plugin.json file you'll need to set `has_intents` and `has_index` to true, you'll also need to define your `main_file`

Example, defining the MessageContent privileged intent

{% code overflow="wrap" %}
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
{% endcode %}
