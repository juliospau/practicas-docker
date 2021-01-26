# Réplica de un servidor simple con Python en Docker hecho por @pablokbs
## Partes

- **1: Servidor**

```python
import http.server
import socketserver

port = 8080
handler = http.server.SimpleHTTPRequestHandler

with socketserver.TCPServer(("", port), handler) as httpd:
    print ("Serving at port", port)
    httpd.serve_forever()
```

- **2: Página de prueba**

```html
<!DOCTYPE html>
<html lang="es">
<head>
	<meta charset="UTF-8">
	<title>Prueba de servidor básico con Python</title>
</head>
<body>
	<p>Página servida con Python en Docker</p>
</body>
</html>
```

- **3: Dockerfile**

```dockerfile
FROM python:3.8-alpine
WORKDIR /usr/src/server
COPY . .
CMD ["python", "server.py"]
```

---

## Pasos

- **1: Generar imagen**

```bash
docker build . -t server-img
```

- **2: Generar contenedor**

```bash
docker run --name servidor-cont -dit -p 8080:8080 server-img
```

## Referencias

- **(DIFERENCIA entre CMD, RUN, y ENTRYPOINT en DOCKER - V2M)[https://www.youtube.com/watch?v=6ZnecM3ipu4]**
- **(Contenedor en DockerHub. Tag: 3.8-alpine)[https://hub.docker.com/_/python]**
