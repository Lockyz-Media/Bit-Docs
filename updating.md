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
This version of Bit will enter End of Support the 4th of July 2025.

This means it will only receive major bug fixing and security updates!
{% endhint %}

### Bit 2024.1 to Bit 2024.2

#### Things to remember

* Make sure ALL plugins are updated to any version from Bit 2024.1-2024.2
  * Bit 2024.1 made major changes to how plugins work, and Bit 2024.2 makes various other changes
* Delete every single file and folder from Bit excluding the plugins folder (though remove the bit-core plugin) and the config.json file

#### Updating config.json

Bit 2024.2 makes use of a new configs folder, simply move you config.json file to /configs/bit

#### Update ALL plugins to their latest versions

All plugins must be updated for use in Bit 2024.1 or Bit 2024.2, however we HIGHLY recommend making sure your plugins work for Bit 2024.2

#### Update your node modules and deploy commands

Open the bot in the terminal of your choice and run the `npm i` command.

Once that is done run `node deploy.js` to deploy the bots commands.

#### And you're done

Aside from plugin-specific updates, you should now be fine to run Bit. Simply use the `node bit.js` command and you're all set!
