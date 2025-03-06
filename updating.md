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

#### Bit 2024.2 to Bit 2025.1 <a href="#bit-2024.1-to-bit-2024.2" id="bit-2024.1-to-bit-2024.2"></a>

**Things to remember**

* Make sure ALL plugins are updated to Bit 2025.1
  * Bit 2025.1 has changed quite a LOT compared to Bit 2024.2
* Delete every single file and folder from Bit excluding the plugins folder (though remove the bit-core plugin). It's HIGHLY recommended to remake your config for this release.

**Updating config.json**

Bit 2025.1 splits up the config file. Please redownload Bits MAIN config file, and update the settings there. This should be located in the Bit folder NOT the config/bit-core folder (which is used for bits update system and can break the bot if touched)

**Update ALL plugins to their latest versions**

All plugins must be updated for use in Bit 2025.1

**Update your node modules and deploy commands**

Open the bot in the terminal of your choice and run the `npm i` command.

Once that is done run `node deploy.js` to deploy the bots commands.

**And you're done**

Aside from plugin-specific updates, you should now be fine to run Bit. Simply use the `node bit.js` command and you're all set!
