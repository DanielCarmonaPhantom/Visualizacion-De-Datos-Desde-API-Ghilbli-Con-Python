# Proyecto_Visualizacion-De-Datos-Desde-Api-Ghilbli-Con-Python
![](https://images8.alphacoders.com/105/thumb-1920-1053126.jpg)

Para este proyecto, se utilizara la documentación de la [Api de Studio Ghilbli](https://ghibliapi.herokuapp.com/) que se encuentra en su versión **1.0.1** y se utilizara **Python** para su extración de datos, **Pandas** para el manejo y **[Matplotly](https://matplotlib.org/?fbclid=IwAR2_L-pd4Ycnjd4WZWuP8us9L4Z07844QQ9gjTHtHD7GskLTeCh-c-03hro)** para su graficación

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

```
response = requests.get(url)

if response.status_code == 200:
    
    films = response.json()
```

# 3. Manejo de datos

Ahora que obtuvimos una respuesta exitosa y obtuvimos de la API los datos de los 'films' podemos manejar de forma más sencilla los datos

```
film
```
```
[
  {'id': '2baf70d1-42bb-4437-b551-e5fed5a87abe',
  'title': 'Castle in the Sky',
  'description': "The orphan Sheeta inherited a mysterious crystal that links her to the mythical sky-kingdom of Laputa. With the help of resourceful Pazu and a rollicking band of sky pirates, she makes her way to the ruins of the once-great civilization. Sheeta and Pazu must outwit the evil Muska, who plans to use Laputa's science to make himself ruler of the world.",
  'director': 'Hayao Miyazaki',
  'producer': 'Isao Takahata',
  'release_date': '1986',
  'rt_score': '95',
  'people': ['https://ghibliapi.herokuapp.com/people/'],
  'species': ['https://ghibliapi.herokuapp.com/species/af3910a6-429f-4c74-9ad5-dfe1c4aa04f2'],
  'locations': ['https://ghibliapi.herokuapp.com/locations/'],
  'vehicles': ['https://ghibliapi.herokuapp.com/vehicles/'],
  'url': 'https://ghibliapi.herokuapp.com/films/2baf70d1-42bb-4437-b551-e5fed5a87abe'}
  ...................
```

Obtenemos la primera pelicula dentro de nuestro json obteniendo su indice

```
films[0]
```

Para obtener un valor dentro de una llave, mandamos a llamar el espacio de su indice y la llave que nos gustaria ver
```
films[0]['title']
```
```
    'Castle in the Sky'
```
