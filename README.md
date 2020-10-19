# Proyecto_Visualizacion-De-Datos-Desde-Api-Ghilbli-Con-Python
![](https://images8.alphacoders.com/105/thumb-1920-1053126.jpg)

Para este proyecto, se utilizara la documentación de la [Api de Studio Ghilbli](https://ghibliapi.herokuapp.com/) que se encuentra en su versión **1.0.1** y se utilizara **python** para su extración de datos, Pandas para el manejo y [Matplotly](https://matplotlib.org/?fbclid=IwAR2_L-pd4Ycnjd4WZWuP8us9L4Z07844QQ9gjTHtHD7GskLTeCh-c-03hro) para su graficación

### Contenido
1. Librerias
2. Requests
3. Manejo de Datos
    1. Iteración de los datos
4. Visualización de datos
    1. Importamos Pandas y Matploly
    2. Obtendremos los films que realizo el director "Hayap Miyazaki"
        1. Evaluaremos la calificación que obtuvo cada film
    3. People
    4. Las mejores 5 películas de studio Ghilbli
    5. Locations
    6. Species
    7. Vehicles

## 1. Librerias

Para consumir la API, utilizaremos la libreria requests

```
import requests
```

## 2. Request

+ Dentro de la documentación, nos indica que debemos utilizar la base url = 'https://ghibliapi.herokuapp.com/' y los **ENDPONTS** que podemos visualizar

    + FILS
    + PEOPLE
    + LOCATION
    + SPECIES
    + VEHICLES
    
Así que para los films utilizaremos la siguiente url:

```
url = 'https://ghibliapi.herokuapp.com/films'
```

Y hacemos la petición y la guardamos en una variable response. Despues validamos si la petición fue existosa evaluando el status.code de nuestra variable siendo 200 (Para más información buscar información sobre las respuestas de response) 

```
response = requests.get(url)

if response.status_code == 200:
  # Your code

```

Asi que guardaremos los datos obtenidos en nuestra variable, haremos una conversion json() 

```
films = response.json()

```

y ahora si, ejecutamos todo este bloque de codigo junto (TARDARA UN POCO EN OBTENER LOS DATOS)
