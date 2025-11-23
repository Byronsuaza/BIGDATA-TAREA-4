📚 Proyecto MongoDB – Análisis de Catálogo de Netflix

Este proyecto implementa una base de datos NoSQL utilizando MongoDB, aplicando operaciones CRUD, consultas avanzadas y agregaciones sobre un dataset real de películas y series de Netflix, obtenido de Kaggle.

El objetivo es demostrar el diseño, carga, manipulación y análisis de datos dentro de un entorno MongoDB, siguiendo las fases solicitadas en el trabajo académico.

📁 Contenido del repositorio
📁 Proyecto-MongoDB  
│── README.md
│── mongodb_comandos_explicados.txt
│── netflix_titles.csv


🧩 1. Diseño de la Base de Datos
✔ Caso de uso

El caso de uso seleccionado es un catálogo de contenido audiovisual, como el utilizado por plataformas tipo Netflix. Este escenario es ideal para una base de datos NoSQL debido a:

La estructura flexible de los datos (no todos los títulos tienen los mismos campos).

Presencia de listas o valores múltiples (cast, países, géneros).

Necesidad de consultas rápidas, escalabilidad y almacenamiento de documentos heterogéneos.

✔ Base de datos utilizada
universidad

✔ Colección principal
estudiante

✔ Estructura del documento (esquema lógico)

Cada documento contiene información como:

{
  "show_id": "s1",
  "type": "Movie",
  "title": "Example Title",
  "director": "Some Director",
  "country": "United States",
  "date_added": "September 25, 2021",
  "release_year": 2020,
  "rating": "PG-13",
  "duration": "90 min",
  "listed_in": "Documentaries",
  "description": "Short description…"
}

🛠️ 2. Implementación en MongoDB
✔ Inserción de datos

Se importaron 8807 documentos en la colección estudiante a través de MongoDB Compass usando el dataset de Kaggle.

También se realizaron inserciones manuales mediante insertOne e insertMany.

✔ Comandos utilizados

Todos los comandos ejecutados se encuentran documentados en:

📄 mongodb_comandos_explicados.txt

Incluyen:

Inserción de datos

Consultas básicas

Consultas con filtros y operadores

Actualizaciones y eliminaciones

Consultas de agregación

Ejemplo de consulta de agregación:

db.estudiante.aggregate([
  { $group: { _id: "$type", total: { $sum: 1 } } }
])

📊 3. Consultas de Agregación y Análisis
✔ Cantidad de películas y series

Permite conocer la distribución del catálogo.

✔ Promedio del año de lanzamiento

Mide la antigüedad promedio del contenido.

✔ Top 5 países con más títulos

Revela los países más representados.

✔ Categorías más frecuentes

Ayuda a conocer el enfoque de contenido de la plataforma.

Todos los resultados están explicados de forma detallada en el documento de comandos.

🧪 4. Resultados Principales

Entre los principales hallazgos:

Hay más películas que series en el catálogo.

Estados Unidos e India son los países con mayor producción.

Los géneros más comunes incluyen:
Drama, Comedia, Documentaries.

El promedio de año de lanzamiento está concentrado en las últimas dos décadas.

Estos resultados muestran la utilidad del modelo NoSQL para análisis rápidos sobre grandes volúmenes de datos documentales.

🚀 5. Tecnologías utilizadas

MongoDB Community / MongoDB Compass

MongoSH (Mongo Shell)

Dataset de Kaggle – Netflix Movies and TV Shows

GitHub para documentación y control de versiones

📝 6. Autor

Byron Eduardo Falla Suaza
Proyecto académico para la Universidad Nacional Abierta y a Distancia (UNAD).

📌 7. Licencia

Este proyecto es de uso educativo. Puedes modificarlo, distribuirlo o reutilizarlo con fines académicos.
