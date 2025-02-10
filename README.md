API desplegada: https://secret-lil-alex-itsaalex-5dd72c8d.koyeb.app/

# API de Noticias

## Descripción
Esta API permite gestionar noticias, incluyendo la creación, eliminación, archivado, restauración y marcación como favoritas.

---

## Modelo de Datos

La API utiliza un esquema de Mongoose para representar una noticia con los siguientes campos:

```javascript
const newsSchema = new mongoose.Schema({
  title: { type: String, required: true },
  image: { type: String, required: true },
  description: { type: String, required: true },
  date: { type: String, required: true },
  content: { type: String, required: true },
  author: { type: String, required: true },
  archiveDate: { type: String, default: null },
  achieved: { type: Boolean, required: true, default: false },
  isFavorite: { type: Boolean, required: true, default: false },
});
```

---

## Endpoints

### 1. Obtener todas las noticias
**GET /news**

#### Respuesta:
```json
[
  {
    "_id": "65a7b3e3a3c9b2d4f0e0a123",
    "title": "Ejemplo de noticia",
    "image": "https://example.com/image.jpg",
    "description": "Breve descripción de la noticia.",
    "date": "2024-02-10",
    "content": "Contenido detallado de la noticia.",
    "author": "Autor Ejemplo",
    "archiveDate": null,
    "achieved": false,
    "isFavorite": false
  }
]
```

---

### 2. Crear una nueva noticia
**POST /news**

#### Cuerpo de la solicitud:
```json
{
  "title": "Nueva noticia",
  "image": "https://example.com/new-image.jpg",
  "description": "Breve descripción de la nueva noticia.",
  "date": "2024-02-10",
  "content": "Contenido completo de la noticia.",
  "author": "Nombre del autor"
}
```

#### Respuesta:
```json
{
  "message": "Noticia creada exitosamente",
  "news": { ... }
}
```

---

### 3. Eliminar una noticia
**DELETE /news/:id**

#### Respuesta:
```json
{
  "message": "Noticia eliminada exitosamente"
}
```

---

### 4. Archivar una noticia
**PUT /news/archive/:id**

#### Respuesta:
```json
{
  "message": "Noticia archivada exitosamente",
  "news": { ... }
}
```

---

### 5. Restaurar una noticia archivada
**PUT /news/restore/:id**

#### Respuesta:
```json
{
  "message": "Noticia restaurada exitosamente",
  "news": { ... }
}
```

---

### 6. Marcar/Desmarcar como favorita
**PUT /news/favorite/:id**

#### Respuesta:
```json
{
  "message": "Estado de favorito actualizado",
  "news": { ... }
}
```

---

## Notas
- Todas las respuestas contienen un objeto `news` con la información actualizada.
- En caso de error, la API responderá con un mensaje adecuado y un código de estado HTTP correspondiente.


