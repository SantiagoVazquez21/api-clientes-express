# API de Clientes — Node.js + Express + Supabase

API REST con el CRUD completo de una tabla de clientes, guardada en Supabase (PostgreSQL) y deployada en Vercel.

**🔗 En vivo:** [parcial-aplicativos-moviles.vercel.app](https://parcial-aplicativos-moviles.vercel.app)

## Endpoints

| Método | Ruta | Qué hace |
| --- | --- | --- |
| `GET` | `/api/clientes` | Lista todos los clientes |
| `POST` | `/api/clientes` | Crea un cliente (`nombre`, `email`, `telefono`) y responde `201` |
| `PUT` | `/api/clientes/:id` | Actualiza un cliente |
| `DELETE` | `/api/clientes/:id` | Elimina un cliente |

Ejemplo:

```bash
curl -X POST https://parcial-aplicativos-moviles.vercel.app/api/clientes \
  -H "Content-Type: application/json" \
  -d '{"nombre":"Ana","email":"ana@mail.com","telefono":"1122334455"}'
```

## Cómo está hecho

```
src/
├── app.js                          # Express: CORS, JSON y montaje de rutas
├── config/database.js              # Cliente de Supabase con las variables de entorno
├── routes/clientesRoutes.js        # Rutas → controladores
└── controllers/clientesController.js  # Consultas a Supabase y respuestas HTTP
```

- Separación en capas: las rutas solo apuntan a controladores y la conexión a la base vive en su propio módulo.
- Credenciales fuera del código con `dotenv` (`.env.example` sin valores).
- Errores de la base devueltos como `500` con el mensaje, y `201` al crear.
- Deploy serverless en Vercel con `vercel.json`.

## Tecnologías

Node.js · Express · Supabase (PostgreSQL) · dotenv · CORS · Vercel

## Correrlo en local

```bash
npm install
cp .env.example .env   # completar SUPABASE_URL y SUPABASE_KEY
npm run dev
```

La API queda en `http://localhost:3000`.

---

Hecho por **Santiago Elian Vazquez** como parcial de la Tecnicatura Superior en Desarrollo de Software (ISFT 225).
[Portfolio](https://santiago-vazquez-portfolio.vercel.app) · [LinkedIn](https://www.linkedin.com/in/santiago-vazquez-b266b3374/)
