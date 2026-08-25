# Ejercicio 6: Definición de un JSON Schema

**Consigna:** Tome el documento que diseñó en el Ejercicio 3 (orden de compra) y escriba su JSON Schema correspondiente. El esquema debe exigir como mínimo: campos obligatorios (required), tipos de dato correctos para cada propiedad, un enum para el campo estado (por ejemplo: "pendiente", "pagado", "enviado", "entregado", "cancelado"), y una validación de mínimo (minimum) para las cantidades y precios (no pueden ser negativos).

```json
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "type": "object",
  "properties": {
    "estado": {
      "type": "string",
      "enum": ["pendiente", "pagado", "enviado", "entregado", "cancelado"]
    },
    "cliente": {
      "type": "object",
      "properties": {
        "nombre": {
          "type": "string"
        },
        "apellido": {
          "type": "string"
        },
        "email": {
          "type": "string"
        },
        "dni": {
          "type": "string"
        }
      },
      "required": ["nombre", "apellido", "email", "dni"]
    },
    "productos_comprados": {
      "type": "array",
      "items": {
        "type": "object",
        "properties": {
          "nombre": {
            "type": "string"
          },
          "cantidad": {
            "type": "integer",
            "minimum": 0
          },
          "precio_unitario": {
            "type": "number",
            "minimum": 0
          }
        },
        "required": ["nombre", "cantidad", "precio_unitario"]
      }
    },
    "direccion_envio": {
      "type": "object",
      "properties": {
        "calle": {
          "type": "string"
        },
        "numero": {
          "type": "string"
        },
        "provincia": {
          "type": "string"
        },
        "pais": {
          "type": "string"
        }
      },
      "required": ["calle", "numero", "provincia", "pais"]
    },
    "total": {
      "type": "number"
    }
  },
  "required": [
    "estado",
    "cliente",
    "productos_comprados",
    "direccion_envio",
    "total"
  ]
}
```
