# Mapas para el Programa de Pago por Servicios Ambientales (PSA) en biodiversidad del año 2024

Este repositorio contiene los documentos, elaborados con el sistema de publicación técnica y científica [Quarto](https://quarto.org/), para la generación de mapas para el Programa de Pago por Servicios Ambientales (PSA) en biodiversidad del año 2024. Los mapas muestran la riqueza de especies de plantas y animales en una grilla de hexágonos. En cada caso, se siguió un flujo de trabajo de tres pasos:

1. Depuración de una lista de especies.
2. Descarga de registros de presencia de las especies de la lista.
3. Generación del mapa de riqueza de especies.

Los documentos Quarto combinan texto con salidas generadas por el lenguaje de programación [R](https://www.r-project.org/). Como parte de la implementación del procesamiento en R, se utilizó el paquete [rgbif](https://cran.r-project.org/web/packages/rgbif/) para acceder los servicios web de la [interfaz de programación de aplicaciones (API) de la Infraestructura Mundial de Información en Biodiversidad (GBIF)](https://www.gbif.org/developer/summary).

## Flujos de trabajo

### Plantas
[Depuración de lista de especies](https://biodatacr.github.io/mapas-psa-biodiversidad-2024/src/data/depuracion-lista-especies-plantas.html) -> [Descarga de registros de presencia de especies](https://biodatacr.github.io/mapas-psa-biodiversidad-2024/src/data/descarga-registros-presencia-especies-plantas.html) -> [Generación de mapa de riqueza de especies](https://biodatacr.github.io/mapas-psa-biodiversidad-2024/src/data/generacion-mapa-riqueza-especies-plantas.html)

### Animales
[Depuración de lista de especies](https://biodatacr.github.io/mapas-psa-biodiversidad-2024/src/data/depuracion-lista-especies-animales.html) -> [Descarga de registros de presencia de especies](https://biodatacr.github.io/mapas-psa-biodiversidad-2024/src/data/descarga-registros-presencia-especies-animales.html) -> [Generación de mapa de riqueza de especies](https://biodatacr.github.io/mapas-psa-biodiversidad-2024/src/data/generacion-mapa-riqueza-especies-animales.html)

## Resultados

### Plantas (fecha de generación: 2024-04-15)
- [Lista depurada de especies de plantas](https://biodatacr.github.io/mapas-psa-biodiversidad-2024/data/processed/lista-final-especies-plantas.csv)  
- [Registros de presencia de especies de plantas](https://biodatacr.github.io/mapas-psa-biodiversidad-2024/data/processed/registros-presencia-especies-plantas.csv)  
- [Mapa de riqueza de especies de plantas](https://biodatacr.github.io/mapas-psa-biodiversidad-2024/data/processed/riqueza-especies-plantas.gpkg)  

### Animales (fecha de generación: 2024-04-15)
- [Lista depurada de especies de animales](https://biodatacr.github.io/mapas-psa-biodiversidad-2024/data/processed/lista-final-especies-animales.csv)  
- [Registros de presencia de especies de animales](https://biodatacr.github.io/mapas-psa-biodiversidad-2024/data/processed/registros-presencia-especies-animales.zip)  
- [Mapa de riqueza de especies de animales](https://biodatacr.github.io/mapas-psa-biodiversidad-2024/data/processed/riqueza-especies-animales.gpkg)  

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