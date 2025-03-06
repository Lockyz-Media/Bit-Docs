---
icon: plug
---

# Plugin Functions

As part of Bit 2025.2 we added a brand new suit of functions to interact with Bits plugin system.

These functions can be imported with the following code at the top of your code

```javascript
const plugins =  require("bit/plugins");
```

Theres a few different functions you can run with this import...

### .is\_active(id, version)

The is\_active function can be used to detect if a plugin is installed, and whether it matches a specific version. This function should be used in conjunction with bits soft-requirements system to block parts of your plugin to users who may not have all the required plugins.

The version paramater is optional and can be ommitted.

```javascript
plugins.is_active(name, version)
```

Example with Bit: Core 2025.2.0 installed

```javascript
const reqMet = plugins.is_active('bit-core', '2025.2.0');

console.log(reqMet)

// Output if everything matches
/*
{
    "installed": true,
    "activated": true,
    "match_version": true
}
*/

// Output if Bit: Core is not installed
/*
{
    "installed": false,
    "activated": null,
    "match_version": null
}
*/

// Output if Bit: Core is installed but not on the right version.
/*
{
    "installed": true,
    "activated": true,
    "match_version": false
}
*/

// Output if Bit: COre is installed but disabled
/*
{
    "installed": true,
    "activated": false,
    "match_version": null
}
*/
```

### .find(id)

`plugins.find(id)` is used to find a specific plugin and it's information.

If the plugin cannot be found within the plugins database, it'll return a status code of 404.

This function will return an array of the plugins info and/or the status of the search.

```javascript
plugins.find(id)
```

Example use

```javascript
const plugins = require('bit/plugins');

const pluginInfo = plugins.find('bit-core')

if(!pluginInfo.status.code === 404) {
    console.log(`Plugin with an id of 'bit-core' cannot be found`)
} else {
    console.log(`Plugin with an id of 'bit-core' was found!`)
    console.log(`Plugin Name: ${pluginInfo.plugin.name}`)
    console.log(`Plugin ID: ${pluginInfo.plugin.id}`)
    console.log(`Plugin Version: ${pluginInfo.plugin.version}`)
    console.log(`Plugin Has Index?: ${pluginInfo.plugin.has_index}`)
    console.log(`Plugin Disabled: ${pluginInfo.plugin.disabled}`)
    console.log(`Plugin Requirements: ${pluginInfo.plugin.requirements}`)
}

// Output if bit-core is found
/*
Plugin with an id of 'bit-core' was found!
Plugin Name: Bit: COre
Plugin ID: bit-core
Plugin Version: 2025.2.0
Plugin Has Index?: true
Plugin Disabled: false
Plugin Requirements: {
    "bit": {
        "version": "2025.2.0",
        "level": 0
    }
}
*/

// Output if bit-core is not found
/*
Plugin with an id of 'bit-core' cannot be found
*/
```

### .list()

Shows a list of all installed plugins

```javascript
plugins.list()
```

{% hint style="danger" %}
UNFINISHED
{% endhint %}

### .count()

Counts all the plugins installed, and outputs the number.

```javascript
plugins.count()
```

Example

```javascript
const plugins = require('bit/plugins');

const count = plugins.count()

console.log(count)

// Output
/* 
0
*/
```
