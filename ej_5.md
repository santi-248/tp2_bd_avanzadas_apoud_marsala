# Ejercicio 5: Embedding vs. Referencing

## Modelo Embebido (Embedded)
En este enfoque, todas las reseñas se guardan como un array de subdocumentos dentro del documento principañ de la película.

```json
{
    "_id": "PEL-001",
    "titulo": "Interestellar",
    "director": "Christopher Nolan",
    "resenas": [
        {
            "usuarioId": "USR-105",
            "comentario": "Una obra maestra",
            "puntaje": 5
        },
        {
            "usuarioId": "USR-267",
            "comentario": "Un poco larga",
            "puntaje": 4
        }
    ]
}

```

## Modelo Referenciado (Referenced)
En este enfoque, las películas y las reseñas viven en colecciones separadas. La reseña guarda el "_id" de la película a la que pertenece (similar a una clave foránea).
* Colección de películas
```json
{
    "_id": "PEL-001",
    "titulo": "Interestellar",
    "director": "Christopher Nolan"
}
```
* Colección de reseñas
```json
{
    "_id": "RES-176",
    "peliculaId": "PEL-001",
    "usuarioId": "USR-105",
    "comentario": "Una obra maestra",
    "puntaje": 5
}
```

## Justificación
Para este caso puntual, la alternativa correcta y recomendada sería el modelo referenciado. Esto es teniendo en cuenta que la consigna del ejercicio nos indica que cada película puede llegar a tener miles de reseñas. Si utilizáramos el modelo embebido, estaríamos agregando cada nueva reseña dentro del documento de la película, lo que nos haría caer en el antipatrón de "array ilimitado". Este patrón es peligroso porque degrada el rendimiento de la base de datos al modificar constantemente el tamaño del documento y eventualmente haría que la película supere el límite máximo de tamaño permitido por MongoDB. Al usar las referencias, las reseñas pueden crecer indefinidamente sin afectar el peso ni la velocidad de lectura del documento de la película.