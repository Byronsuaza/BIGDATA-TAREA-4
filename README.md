# 📘 Proyecto MongoDB – Análisis de Catálogo de Netflix

Este proyecto implementa una base de datos NoSQL utilizando MongoDB para almacenar, consultar y analizar un catálogo de películas y series provenientes del dataset **Netflix Movies and TV Shows**.

El objetivo es aplicar operaciones CRUD, consultas avanzadas, filtros y agregaciones, como parte del desarrollo académico.

---

## 📁 Contenido del Repositorio

```
Proyecto-MongoDB/
│── README.md
│── mongodb_comandos_explicados.txt
│── netflix_titles.csv

```

---

# 1. Diseño de la Base de Datos

## 1.1 Caso de uso seleccionado

El caso de uso es un **catálogo de contenido audiovisual**, ideal para MongoDB por:

* Estructuras flexibles (no todos los registros tienen los mismos campos)
* Campos multivaluados (cast, géneros, países)
* Manejo eficiente de grandes volúmenes de datos
* Consultas rápidas y escalables

---

## 1.2 Base de datos y colección

| Elemento      | Nombre        |
| ------------- | ------------- |
| Base de datos | `universidad` |
| Colección     | `estudiante`  |

---

## 1.3 Esquema lógico del documento

Cada documento almacena información como:

```json
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
  "description": "Short description..."
}
```

---

# 2. Implementación en MongoDB

La base de datos fue creada e importada mediante **MongoDB Compass**, cargando **8807 documentos** del dataset.

Adicionalmente, se realizaron inserciones manuales, consultas y agregaciones mediante **MongoSH**.

---

## 2.1 Operaciones CRUD (Mongo Shell)

### Insertar documentos (insertMany)

```js
db.estudiante.insertMany([
  { show_id: "t10000", type: "Movie", title: "Demo Movie", release_year: 2023 },
  { show_id: "t10001", type: "TV Show", title: "Demo Series", release_year: 2021 }
])
```

### Consultar documentos

```js
db.estudiante.find().limit(5)
```

### Actualizar documentos

```js
db.estudiante.updateOne(
  { show_id: "t20000" },
  { $set: { title: "Updated Movie Example" } }
)
```

### Eliminar documentos

```js
db.estudiante.deleteOne({ show_id: "t20000" })
```

---

## 2.2 Consultas con filtros

```js
db.estudiante.find({ release_year: 2020 })
db.estudiante.find({ rating: "TV-MA" })
db.estudiante.find({ release_year: { $gt: 2020 } })
db.estudiante.find({ country: { $in: ["United States", "Canada"] } })
```

---

## 2.3 Consultas de agregación

### Contar películas y series

```js
db.estudiante.aggregate([
  { $group: { _id: "$type", total: { $sum: 1 } } }
])
```

### Promedio del año de lanzamiento

```js
db.estudiante.aggregate([
  { $group: { _id: null, promedio: { $avg: "$release_year" } } }
])
```

### Top 5 países con más títulos

```js
db.estudiante.aggregate([
  { $group: { _id: "$country", total: { $sum: 1 } } },
  { $sort: { total: -1 } },
  { $limit: 5 }
])
```

### Categorías más comunes

```js
db.estudiante.aggregate([
  { $group: { _id: "$listed_in", total: { $sum: 1 } } },
  { $sort: { total: -1 } },
  { $limit: 10 }
])
```

---

# 3. Resultados del análisis

* El catálogo contiene una mayor proporción de películas comparado con series.
* Estados Unidos e India son los países con más títulos.
* Los géneros predominantes incluyen dramas, comedias y documentales.
* La mayoría del contenido fue producido en los últimos 20 años.

---

# 4. Tecnologías utilizadas

* MongoDB Compass
* MongoSH
* JavaScript para consultas
* Dataset de Kaggle
* GitHub

---

# 5. Autor

**Byron Falla Suaza**
Proyecto académico — UNAD (Universidad Nacional Abierta y a Distancia)

