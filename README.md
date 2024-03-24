# Mapas para el Programa de Pago por Servicios Ambientales (PSA) en biodiversidad del año 2024

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
docker run -d --name biodatacr-r-433 \
  -p 8787:8787 \
  -v /home/mfvargas/biodatacr/github/mapas-psa-biodiversidad-2024:/home/rstudio \
  -e PASSWORD=biodatacr \
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
