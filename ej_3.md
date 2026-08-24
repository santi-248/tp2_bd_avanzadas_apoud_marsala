# Ejercicio 3: Documento con anidamiento profundo

**Consigna:** Modele un pedido de e-commerce ("orden de compra") que contenga: datos del cliente (anidado), una lista de productos comprados (array de objetos, cada uno con nombre, cantidad y precio unitario), una dirección de envío (objeto anidado) y el estado del pedido. Calcule y agregue un campo total coherente con los ítems.

```json
{
  "estado": "Pendiente",
  "cliente": {
    "nombre": "Juan",
    "apellido": "Pérez",
    "email": "juan.perez@example.com",
    "dni": "2212345678"
  },
  "productos_comprados": [
    {
      "nombre": "Teclado Mecánico",
      "cantidad": 1,
      "precio_unitario": 80000
    },
    {
      "nombre": "Mouse",
      "cantidad": 2,
      "precio_unitario": 25000
    },
    {
      "nombre": "Mousepad",
      "cantidad": 1,
      "precio_unitario": 20000
    }
  ],
  "direccion_envio": {
    "calle": "San Martín",
    "numero": "102B",
    "provincia": "Mendoza",
    "pais": "Argentina"
  },
  "total": 150000
}
```
