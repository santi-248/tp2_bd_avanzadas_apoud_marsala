# Ejercicio 7: Caso integrador — modelado de un e-commerce

## 1. Un documento de ejemplo válido

**Colección Usuarios**

```json
{
  "_id": "USR-001",
  "nombre": "Santiago",
  "email": "santiago@email.com",
  "direccionEnvio": {
    "calle": "San Martín 123",
    "ciudad": "Maipú, Mendoza",
    "codigoPostal": "M5515"
  }
}
```

**Colección Productos**

```json
{
  "_id": "PROD-102",
  "nombre": "Kingston NV3 500GB SSD",
  "categoria": "Componentes de PC",
  "precio": 52000,
  "stock": 15
}
```

**Colección Pedidos**

```json
{
  "_id": "PED-8832",
  "usuarioId": "USR-001",
  "fecha": "2026-08-23",
  "estado": "pagado",
  "items": [
    {
      "productoId": "PROD-102",
      "nombre": "Kingston NV3 500GB SSD",
      "cantidad": 1,
      "precioUnitario": 52000
    }
  ],
  "total": 52000
}
```

## 2. Justificación de Relaciones

**Relación Pedido-Usuario (Referenciada)**
Se utilizó el modelo referenciado guardando únicamente el usuarioId en el pedido. Esto se debe a que la entidad usuario es compartida por muchos pedidos (evita la duplicación de datos) y su información se actualiza de forma independiente (por ejemplo, si el usuario cambia su contraseña o email).
**Relación Pedido-Producto (Híbrida / Embebida)**
Se utilzó un modelo embebido para los ítems dentro del pedido. Aunque el producto existe en su propia colección, en el pedido se embebe una "captura" de los datos clave (nombre y precio) al momento de la compra. Esta es una relación de composición fuerte: los datos embebidos se consultan junto con el pedido principal. Además, garantiza que si el precio del producto cambia en la base de datos en el futuro, el total de ese pedido histórico no se vea afectado.

## 3. JSON Schema

```json
{
  "$schema": "[http://json-schema.org/draft-07/schema#](http://json-schema.org/draft-07/schema#)",
  "title": "Producto",
  "type": "object",
  "required": ["nombre", "categoria", "precio"],
  "properties": {
    "nombre": {
      "type": "string",
      "minLength": 3
    },
    "categoria": {
      "type": "string"
    },
    "precio": {
      "type": "number",
      "minimum": 0
    },
    "stock": {
      "type": "integer",
      "minimum": 0
    }
  },
  "additionalProperties": false
}
```
