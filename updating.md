---
icon: desktop-arrow-down
layout:
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: false
---

# Updating

{% hint style="warning" %}
This version of Bit will enter End of Support the 23rd of April 2025.

This means it will only receive major bug fixing and security updates!
{% endhint %}

### Bit 5.2 to Bit 2024.1

#### Things to remember

* Make sure ALL plugins are updated to 2024.1
  * Bit 2024.1 makes MAJOR changes to the bots command handler. Things WILL break
* Make sure to delete all the Bit and Bit Core files. This means EVERYTHING bar the /plugins folder and then everything inside the /plugins/bit-core folder!

#### Updating config.json

All config options are in snake case now. Please see the example below!

The config now requires a guild\_only, language and dev\_only field, you can follow the format below (using their default values)

```
"guildOnly": false,
"language": "en",
"devmode": false
```

Currently, language can only be "en".

Example

```json
{
    "embed_colours": {
        "positive": "#00FF1C",
        "negative": "#FF0000",
        "neutral": "#9013FE",
        "main": "#86C1FD",
        "secondary": "#50E3C2"
    },
    "botIDs": {
        "logs": "LOGGING ID",
        "guild": "GUILD ID",
        "client": "CLIENT/APPLICATION ID",
        "owner": "OWNER ID"
    },
    "activities": {
        "type": "custom, playing, listening or watching",
        "state": "The text that displays as the status",
        "status": "online, idle, invisible or dnd"
    },
    "guildOnly": false,
    "language": "en",
    "devmode": false,
    "token": "BOT TOKEN"
}
```
