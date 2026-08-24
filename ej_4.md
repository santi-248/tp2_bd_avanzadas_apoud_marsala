# Ejericio 4: Array de subdocumentos — caso biblioteca

**Consigna:** Diseñe el documento JSON de un "libro" que incluya un array de autores (cada autor con nombre y país) y un array de categorías/géneros (strings simples). Justifique en un párrafo por qué los autores se modelaron como array de objetos y las categorías como array de strings.

```json
{
  "autores": [
    { "nombre": "Jorge Luis Borges", "pais": "Argentina" },
    { "nombre": "Julio Cortázar", "pais": "Argentina" },
    { "nombre": "Alejandra Pizarnik", "pais": "Argentina" },
    { "nombre": "Alfonsina Storni", "pais": "Argentina" }
  ],
  "categorías": ["Realismo Mágico", "Terror", "Romance", "Policial"]
}
```

## Justificación

Cuando tenemos un atributo con uno o más sub-atributos, debemos utilizar anidación con objetos. Esto tanto poder relacionar los datos hijos con su padre, como para poder leerlos de forma organizada, como es el caso de los autores en la consigna. Por otro lado, cuando tenemos un atributo que podría poseer varios valores simples, que es el caso de los géneros literarios, la anidación se vuelve innecesaria. Entonces podemos agrupar las categorías como una lista/array de strings.
