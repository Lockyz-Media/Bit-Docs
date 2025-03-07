# bit/plugins

Como parte de Bit 2025.2 agregamos un nuevo conjunto de funciones para interactuar con el sistema de complementos de Bits.

Estas funciones se pueden importar con el siguiente código en la parte superior de su código

```javascript
const plugins =  require("bit/plugins");
```

Hay algunas funciones diferentes que puedes ejecutar con esta importación...

### .is\_active(id, versión)

La función is\_active se puede utilizar para detectar si un complemento está instalado y si coincide con una versión específica. Esta función se debe utilizar junto con el sistema de requisitos de software de bits para bloquear partes de su complemento a los usuarios que pueden no tener todos los complementos necesarios.

El parámetro de versión es opcional y se puede omitir.

```javascript
plugins.is_active(id, versión)
```

Ejemplo con Bit: Core 2025.2.0 instalado

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

plugins.find(id) se utiliza para buscar un complemento específico y su información.

Si no se puede encontrar el complemento en la base de datos de complementos, devolverá un código de estado 404.

Esta función devolverá una matriz con la información del complemento y/o el estado de la búsqueda.

```javascript
plugins.find(id)
```

Ejemplo de uso

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

Muestra una lista de todos los complementos instalados

```javascript
plugins.list()
```

{% hint style="danger" %}
INCONCLUSO
{% endhint %}

### .count()

Cuenta todos los complementos instalados y genera el número.

```javascript
plugins.count()
```

Ejemplo

```javascript
const plugins = require('bit/plugins');

const count = plugins.count()

console.log(count)

// Output
/* 
0
*/
```
