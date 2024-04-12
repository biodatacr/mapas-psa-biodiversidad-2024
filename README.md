# Mapas para el Programa de Pago por Servicios Ambientales (PSA) en biodiversidad del año 2024

Este repositorio contiene el código fuente para la generación de mapas para el Programa de Pago por Servicios Ambientales (PSA) en biodiversidad del año 2024.

## Flujos de trabajo

### Plantas

[Depuración de lista de especies](https://biodatacr.github.io/mapas-psa-biodiversidad-2024/src/data/depuracion-lista-especies-plantas.html) -> \
[Descarga de registros de presencia de especies](https://biodatacr.github.io/mapas-psa-biodiversidad-2024/src/data/descarga-registros-presencia-especies-plantas.html) -> \
[Generación de mapa de riqueza de especies](https://biodatacr.github.io/mapas-psa-biodiversidad-2024/src/data/generacion-mapa-riqueza-especies-plantas.html)

### Animales
[Depuración de lista de especies](https://biodatacr.github.io/mapas-psa-biodiversidad-2024/src/data/depuracion-lista-especies-animales.html) -> \
[Descarga de registros de presencia de especies](https://biodatacr.github.io/mapas-psa-biodiversidad-2024/src/data/descarga-registros-presencia-especies-animales.html) -> \
[Generación de mapa de riqueza de especies](https://biodatacr.github.io/mapas-psa-biodiversidad-2024/src/data/generacion-mapa-riqueza-especies-animales.html)

## Resultados
- [Mapa de riqueza de especies de plantas]()  
- [Mapa de riqueza de especies de animales]()  
\
- [Registros de presencia de especies de plantas]()  
- [Registros de presencia de especies de animales]()  

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