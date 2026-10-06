# Tarea 4: Agenda React

**Curso:** Programación WEB · ITLA · 2026-C-003
**Profesor:** Raydelto Hernández
**Estudiante:** _Tu nombre y matrícula aquí_

Agenda de contactos hecha con **React**. Es la versión en React de la Tarea 3
(Agenda Multicapas): mismo diseño y mismas funciones, pero dividida en
componentes.

## Qué hace

- Muestra la lista de contactos guardados, ordenados y agrupados por la inicial del nombre.
- Permite buscar por nombre, apellido o teléfono.
- Permite agregar nuevos contactos (nombre, apellido y teléfono).
- Tiene botón **Recargar** y muestra mensajes de carga, éxito y error.

Los datos se obtienen del servicio web `http://www.raydelto.org/agenda.php`:

| Operación | Método HTTP | Detalle |
|-----------|-------------|---------|
| Listar contactos | `GET` | Devuelve el listado en formato JSON |
| Agregar contacto | `POST` | Cuerpo JSON con `nombre`, `apellido` y `telefono` |

## Componentes

```
App (padre)
├── ListaContactos     → búsqueda, listado agrupado y botón Recargar
└── AgregarContacto    → formulario para agregar contactos
```

- **`App.jsx`**: componente padre. Guarda el estado (`contactos`, `cargando`, `error`) y hace las llamadas `fetch` (GET y POST).
- **`ListaContactos.jsx`**: recibe los datos por props; filtra, ordena y agrupa los contactos.
- **`AgregarContacto.jsx`**: formulario con inputs controlados; valida y avisa al padre con `onAgregar`.

## Estructura del proyecto

```
agenda-react/
├── index.html
├── package.json
├── vite.config.js
└── src/
    ├── main.jsx
    ├── App.jsx
    ├── ListaContactos.jsx
    ├── AgregarContacto.jsx
    └── App.css
```

## Cómo ejecutarlo

Requisito: tener instalado [Node.js](https://nodejs.org).

```bash
npm install
npm run dev
```

Luego abre en el navegador la dirección que muestra la terminal
(normalmente `http://localhost:5173`).

Para generar la versión de producción:

```bash
npm run build
```

## Notas

- El servicio usa `http` (no `https`). Si la app se publica en un sitio `https`, el navegador bloqueará las peticiones por contenido mixto. Por eso se ejecuta de forma local.
- En modo desarrollo, `React.StrictMode` ejecuta los efectos dos veces, por lo que puede verse un GET doble al abrir la página. En producción ocurre una sola vez.

## Tecnologías

React 18 · Vite · JavaScript (ES6+) · CSS3
