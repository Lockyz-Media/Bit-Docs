---
icon: shield-exclamation
---

# Requisitos del complemento

Si su complemento utiliza funciones de otro complemento, puede asegurarse de advertir al usuario haciendo uso del sistema de requisitos de complementos de Bits.

## Configuración

Dentro del archivo plugin.json de sus complementos puede encontrar un campo para definir los requisitos de sus complementos; estos requisitos se enumerarán cuando el complemento se cargue en bit y cuando ejecute el comando plugins.

```json
{
    "requirements": {
        "bit": {
            "version": "2025.1.0",
            "level": 0
        },
        "jupiter": {
            "version": "2025.1.0",
            "level": 2
    }
}
```

Un ejemplo de un complemento que requiere Bit y Jupiter

## Niveles de requisitos

Hay 4 niveles diferentes de requisitos de Bit, que se pueden usar para evitar que el complemento se cargue si el complemento y la versión específica no están presentes, y se pueden usar para evitar que el complemento se cargue si el complemento ESTÁ presente.

Nivel 0, requiere que el complemento externo en esa versión específica se cargue para que su complemento funcione. Nivel 1, requiere que el complemento externo se cargue independientemente de la versión de dicho complemento externo. Nivel 2, es básicamente un requisito flexible, el complemento externo no es "obligatorio", pero parte de su complemento no funcionará sin él. (Debe incluir una verificación para esto en su código, sin embargo, se agregará una función a Bit Core para ayudar en esto en el futuro). Nivel 3, el complemento NO se iniciará si también se carga un complemento de este nivel. Esto se puede usar para complementos que no sean compatibles con el suyo.
