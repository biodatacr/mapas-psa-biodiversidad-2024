# Mapas para el Programa de Pago por Servicios Ambientales (PSA) en biodiversidad del año 2024

## Depuración de datos
[Lista de especies de plantas](https://biodatacr.github.io/mapas-psa-biodiversidad-2024/src/data/depuracion-lista-especies-plantas.html)

## Comandos para el manejo de la imagen y del contenedor Docker

### Generación de la imagen a partir del archivo Dockerfile
```shell
# Generación de la imagen Docker a partir del archivo Dockerfile
docker build -t biodatacr-r-433 .
```

### Ejecución del contenedor
```shell
# Ejecución del contenedor Docker
# (el directorio local debe especificarse en la opción -v)
# (el archivo con variables de ambiente debe especificarse en la opción --env-file)
docker run -d --name biodatacr-r-433 \
  -p 8787:8787 \
  -v /home/mfvargas/biodatacr/github/mapas-psa-biodiversidad-2024:/home/rstudio \
  --env-file /home/mfvargas/biodatacr-r-433.env \
  biodatacr-r-433
```
  
### Acceso al contenedor (username=rstudio, password=biodatacr)
[http://localhost:8787](http://localhost:8787)

### Detención, inicio y borrado del contenedor
```shell
# Detención del contenedor Docker
docker stop biodatacr-r-433

# Inicio del contenedor Docker
docker start biodatacr-r-433

# Borrado del contenedor Docker
docker rm biodatacr-r-433
```

### Ejemplo de contenido del archivo `biodatacr-r-433.env`
(deben asignarse valores adecuados a las variables)
```shell
# Clave para ingresar a RStudio
PASSWORD=biodatacr

# Variables para acceso al API de GBIF
GBIF_USER=usuario_gbif
GBIF_PWD=clave_gbif
GBIF_EMAIL=correo_gbif
```