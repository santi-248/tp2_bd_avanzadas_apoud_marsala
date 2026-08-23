# Ejercicio 1: JSON mal formado - detección y corrección

## (a) Errores encontrados y justificación

* **Booleano en mayúscula (`"activo": True,`):** En JSON, el valor lógico debe ir siempre en minúsculas (`true` o `false`).
* **Clave sin comillas (`nombre:`):** Las claves (keys) de un objeto deben ir obligatoriamente encerradas entre comillas dobles.
* **Uso de comillas simples (`'Carlos Ruiz'`):** En JSON los strings utilizan comillas dobles, las comillas simples no son válidas.
* **Llave de cierre mal ubicada (`}`):** La llave que cierra el objeto está en el medio del documento, cortando la estructura antes de declarar el resto de las propiedades.
* **Coma sobrante en el array (`["vip", "mayorista",]`):** Hay una coma después del último elemento del array, lo cual se conoce como "trailing comma" y no está permitido.
* **Fecha sin formato de texto (`2026-01-15`):** JSON no posee un tipo de dato nativo para las fechas, por lo que deben representarse como strings (entre comillas dobles).
* **Coma al final del documento (`"ultimaCompra": "...",`):** No se permite dejar una coma después del último par clave/valor del objeto.

## (b) JSON corregido

```json
{
    "activo": true,
    "nombre": "Carlos Ruiz",
    "puntaje": 8.5,
    "tags": [
        "vip",
        "mayorista"
    ],
    "ultimaCompra": "2026-01-15"
}

```