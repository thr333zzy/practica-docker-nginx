# practica-docker-nginx

Servidor web Nginx local con Docker Compose. El directorio `src` se monta en `/usr/share/nginx/html`, así que Nginx sirve `src/index.html` sin reconstruir la imagen.

## Qué hay en el repo

- `src/index.html` — página con el texto **Hola mundo**
- `docker-compose.yml` — servicio `web` con la imagen `nginx:alpine`, el puerto del host `8091` hacia el `80` del contenedor, y el volumen `./src:/usr/share/nginx/html`

## Cómo levantarlo

Hace falta Docker Engine y el plugin Compose.

```bash
docker compose up -d
```

Abre [http://localhost:8091](http://localhost:8091). Debes ver **Hola mundo**.

Para comprobarlo desde la terminal:

```bash
docker compose ps
curl -s http://127.0.0.1:8091
```

Para pararlo:

```bash
docker compose down
```

Si cambias `src/index.html`, recarga el navegador. El volumen ya apunta a ese directorio, no hace falta reconstruir el contenedor.
