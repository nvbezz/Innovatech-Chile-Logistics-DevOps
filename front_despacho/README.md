# Frontend - Innovatech Chile

Aplicación React para gestión de despachos y ventas. Construida con Vite 5 y TailwindCSS, se conecta a los backends mediante axios.

## Tecnologías

- React 18 + Vite 5
- TailwindCSS 3
- Axios, React Router DOM 6, SweetAlert2

## Desarrollo local

```bash
npm install
npm run dev
```

Disponible en `http://localhost:5173`.

## Build de producción

```bash
npm run build
```

Genera la carpeta `dist/` que sirve Nginx en el contenedor Docker.

## Docker

```bash
docker build -t innovatech-frontend .
docker run -p 80:80 innovatech-frontend
```

## Estructura

```
src/
├── assets/
├── componentes/
├── Routes/
└── main.jsx
```

## APIs consumidas

- `GET/POST/PUT/DELETE /api/v1/despachos`
- `GET/POST/PUT/DELETE /api/v1/ventas`
