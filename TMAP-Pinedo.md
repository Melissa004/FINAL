LIBRARY TMAP
================
Pinedo Cienfuegos, Diana Melissa
31/1/2022

## TMAP

**Facilita en la realizacion de mapas tematicos, con funciones estetica
atributo entre otras**

-   Utilizaremos las librerias “tmap” para realizar el mapa tematico y
    “sf” para el manejo de datos vectoriales

``` r
library(tmap)
```

    ## Warning: package 'tmap' was built under R version 4.1.2

``` r
library(sf)
```

    ## Warning: package 'sf' was built under R version 4.1.2

    ## Linking to GEOS 3.9.1, GDAL 3.2.1, PROJ 7.2.1; sf_use_s2() is TRUE

``` r
setwd("C:/Users/edgar/Desktop/IV CICLO/MOQUEGUA")
dir()
```

    ##  [1] "Moquegua.cpg"  "Moquegua.dbf"  "Moquegua.prj"  "Moquegua.qpj" 
    ##  [5] "Moquegua.shp"  "Moquegua.shx"  "myshp.png"     "README.md"    
    ##  [9] "Script_Tmap.R" "tmap.Rproj"

-   Lectura del archivo shapefile dentro de R

moquegua \<- st_read(“Moquegua.shp”) moquegua

moquegua

**ALGUNAS DE LAS FUNCIONES UTILIZADAS**

-   Para mapa tematico rápico

tm_shape(moquegua) + tm_polygons()

-   Agregando y modificando funciones

tm_shape(moquegua) + tm_polygons(‘TAnalfab’, style = ‘quantile’)

-   Función “tm_facets” Sirve para modificar y manipular las diferentes
    vistas que se dan de los mapas

tm_shape(moquegua) + tm_polygons(c(“TAnalfab”,
“Pobreza”,“salud19”,“edu_19”)) + tm_facets(sync = TRUE, ncol = 4)

-   Función “tmap_mode(”view”)” permite manipular las vistas del mapa de
    manera dinámica.

tmap_mode(“view”)

tm_shape(moquegua) + tm_polygons(c(“TAnalfab”, “Pobreza”)) +
tm_facets(sync = TRUE, ncol = 2)

-   OpenTopoMap(). Stamen.Watercolor

Funciones esteticas ### tm_fill() / tm_borders()

tm_shape(moquegua) + tm_fill(col=“TAnalfab”, style=“kmeans”)+
tm_borders(“red”, alpha=1)

## Con la data “World” y “metro”

### tm_dots() / tm_bubbles() / tm_squares() / tm_markers()

data(“World”) data(“metro”)

tm_shape(World) + tm_polygons(“HPI”) + tm_shape(metro) + tm_dots()

tm_shape(World) + tm_polygons(“HPI”) + tm_shape(metro) +
tm_bubbles(size=.2, col=“blue”)

tm_shape(World) + tm_polygons(“HPI”) + tm_shape(metro) +
tm_squares(size=.1, col=“blue”)

tm_shape(World) + tm_polygons(“HPI”) + tm_shape(metro) +
tm_markers(size=.08)
