# Ejercicio 2: Modelado de una entidad simple

## JSON de un estudiante de BD Avanzadas

```json
{
    "nombre": "Santiago",
    "carrera": "Tecnicatura Universitaria en Desarrollo de Software",
    "institucion": "ITU Sede Central",
    "cursandoActualmente": true,
    "calificacionBasesDeDatos": 92.5,
    "contacto": {
        "email": "santiago@itu.com",
        "ciudad": "Mendoza"
    },
    "lenguajesEstudiados": ["Python", "Java", "C++", "SQL"],
    "fechaGraduacion": null
}

```

## Justificación del null
El atributo fechaGraduacion se definió con el valor null porque representa a un estudiante que se encuentra cursando la materia de manera activa. Al no haber finalizado sus estudios todavía, la fecha exacta de egreso es un dato desconocido o inexistente al momento de registrar la entidad en la base de datos.