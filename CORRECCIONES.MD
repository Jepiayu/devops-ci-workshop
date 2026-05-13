# Correcciones

**Integrantes:**
- Nombre 1: Juan david Moreno
- Nombre 2: Jordan Epiayu Gonzalez

## Error 1
- **Archivo:** `requirements.txt`
- **Problema:** `pytest` no estaba listado como dependencia, por lo que no se podía ejecutar los tests
- **Solución:** Se agregó `pytest` al archivo

## Error 2
- **Archivo:** `app.py`
- **Problema:** El endpoint `/` retornaba `"status": "ok"` pero el test esperaba `"status": "running"`
- **Solución:** Se cambió `"ok"` por `"running"`

## Error 3
- **Archivo:** `app.py`
- **Problema:** El endpoint `/health` no incluía el campo `uptime_seconds` en la respuesta JSON
- **Solución:** Se importó el módulo `time`, se creó la variable `START_TIME` al inicio y se calculó el uptime en el endpoint

## Error 4
- **Archivo:** `app.py`
- **Problema:** El endpoint estaba definido como `/metric` en vez de `/metrics`
- **Solución:** Se renombró la ruta y la función a `/metrics` y `def metrics()`

## Error 5
- **Archivo:** `app.py`
- **Problema:** El puerto estaba configurado en `5001` en vez de `5000`
- **Solución:** Se cambió `port=5001` por `port=5000`

## Error 6
- **Archivo:** `Dockerfile`
- **Problema:** Se usaba la imagen base `python:3.11` que es muy pesada
- **Solución:** Se cambió a `python:3.11-slim` para optimizar el tamaño de la imagen

## Error 7
- **Archivo:** `docker-compose.yml`
- **Problema:** El mapeo de puertos era `"5000:5001"`, siendo que la app corre en el puerto `5000` dentro del contenedor
- **Solución:** Se cambió a `"5000:5000"`

## Error 8
- **Archivo:** `prometheus.yml`
- **Problema:** El target estaba configurado como `localhost:5000`, lo cual no funciona dentro de Docker Compose ya que los servicios se comunican por nombre de servicio
- **Solución:** Se cambió a `api:5000`

## Error 9
- **Archivo:** `prometheus.yml`
- **Problema:** El `metrics_path` estaba configurado como `/metric` en vez de `/metrics`
- **Solución:** Se cambió a `/metrics`

## Error 10
- **Archivo:** `.github/workflows/ci.yml`
- **Problema:** Los curl usaban `-s` que ignora errores HTTP, y faltaba testear el endpoint `/`
- **Solución:** Se cambió `-s` por `-f` en todos los curl y se agregó el test del endpoint `/`