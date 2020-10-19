# Proyecto_Visualizacion-De-Datos-Desde-API-Ghilbli-Con-Python
![](https://images8.alphacoders.com/105/thumb-1920-1053126.jpg)

Para este proyecto, se utilizara la documentación de la [API de Studio Ghilbli](https://ghibliapi.herokuapp.com/) que se encuentra en su versión **1.0.1** y se utilizara **Python** para su extración de datos, **Pandas** para el manejo y **[Matplotly](https://matplotlib.org/?fbclid=IwAR2_L-pd4Ycnjd4WZWuP8us9L4Z07844QQ9gjTHtHD7GskLTeCh-c-03hro)** para su graficación

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

### 3.1 Iteración de los datos

Ahora que tenemos los datos y sabemos como obtener datos por su indice y llave, podemos iterar para obtener datos interesantes

#### Obten er longitud total de películas que existen
```
len(films)
```
```
20
```

Aunque son 22, en la Api solo muestran 20

¿Cómo podemos saber cuales son las películas que si hay?

#### Obtener todas las películas

```
for film in films:
    print(film['title'])
```
```
Castle in the Sky
Grave of the Fireflies
My Neighbor Totoro
Kiki's Delivery Service
Only Yesterday
Porco Rosso
Pom Poko
Whisper of the Heart
Princess Mononoke
My Neighbors the Yamadas
Spirited Away
The Cat Returns
Howl's Moving Castle
Tales from Earthsea
Ponyo
Arrietty
From Up on Poppy Hill
The Wind Rises
The Tale of the Princess Kaguya
When Marnie Was There
```

## 4. Visualización de datos.

A partir de aqui termina la explicación de como mandar a llamar la API y como manejar los datos.

### 4.1 Importamos Pandas y Matploly

```
import pandas as pd
```
```
import matplotlib.pyplot as plt
%matplotlib inline
```
Hare las peticiones a todos los endspoints
```
urlFilms = 'https://ghibliapi.herokuapp.com/films'
urlPeople = 'https://ghibliapi.herokuapp.com/people'
urlLocation = 'https://ghibliapi.herokuapp.com/locations'
urlSpecies = 'https://ghibliapi.herokuapp.com/species'
urlVehicles = 'https://ghibliapi.herokuapp.com/vehicles'
```
y guardare la respuiesta en las variables para poder manipular todos nuestros datos.
```
%%time
response1 = requests.get(urlFilms)
response2 = requests.get(urlPeople)
response3 = requests.get(urlLocation)
response4 = requests.get(urlSpecies)
response5 = requests.get(urlVehicles)

films = response1.json()
people = response2.json()
location = response3.json()
species = response4.json()
vehicles = response5.json()
```

Transformo en dataframe una variable 

```
df = pd.DataFrame(films)
df
```

|title  | description | director | release_date | rt_score  | 
| ------------- | ------------- | ------------- | ------------- | ------------- | 
| Castle in the Sky  | The orphan Sheeta inherited a mysterious crystal that links her to the mythical sky-kingdom of Laputa. With the help of resourceful Pazu and a rollicking band of sky pirates, she makes her way to the ruins of the once-great civilization. Sheeta and Pazu must outwit the evil Muska, who plans to use Laputa's science to make himself ruler of the world. | Hayao Miyazaki  | 1986  | 95  | 
| My Neighbor Totoro  | wo sisters move to the country with their father in order to be closer to their hospitalized mother, and discover the surrounding trees are inhabited by Totoros, magical spirits of the forest. When the youngest runs away from home, the older sister seeks help from the spirits to find her.  | Hayao Miyazaki  | 1988  | 93  | 
| Kiki's Delivery Service | A young witch, on her mandatory year of independent life, finds fitting into a new community difficult while she supports herself by running an air courier service.  | Hayao Miyazaki  | 1989  | 96  | 
| Whisper of the Hear  | Shizuku lives a simple life, dominated by her love for stories and writing. One day she notices that all the library books she has have been previously checked out by the same person: 'Seiji Amasawa'. Curious as to who he is, Shizuku meets a boy her age whom she finds infuriating, but discovers to her shock that he is her 'Prince of Books'. As she grows closer to him, she realises that he merely read all those books to bring himself closer to her. The boy Seiji aspires to be a violin maker in Italy, and it is his dreams that make Shizuku realise that she has no clear path for her life. Knowing that her strength lies in writing, she tests her talents by writing a story about Baron, a cat statuette belonging to Seiji's grandfather.  | Yoshifumi Kondō  | 1995 | 91  | 
| Princess Mononoke  |Ashitaka, a prince of the disappearing Ainu tribe, is cursed by a demonized boar god and must journey to the west to find a cure. Along the way, he encounters San, a young human woman fighting to protect the forest, and Lady Eboshi, who is trying to destroy it. Ashitaka must find a way to bring balance to this conflict.  | Hayao Miyazaki  |1997  | 92  | 
| Spirited Away  | Spirited Away is an Oscar winning Japanese animated film about a ten year old girl who wanders away from her parents along a path that leads to a world ruled by strange and unusual monster-like animals. Her parents have been changed into pigs along with others inside a bathhouse full of these creatures. Will she ever see the world how it once was? | Hayao Miyazaki  | 2001  | 97  | 

* Ahora que tenemos los datos, podemos saber varios insights:
    * Directores de cada pelicula
    * El score que tuvo cada película

### 4.2.1 Obtendremos los films que realizo el director "Hayap Miyazaki"
```
df.director
```

```
0.           Hayao Miyazaki
1.            Isao Takahata
2.           Hayao Miyazaki
3.           Hayao Miyazaki
4.            Isao Takahata
5.           Hayao Miyazaki
6.            Isao Takahata
7.         Yoshifumi Kondō
8.          Hayao Miyazaki
9.           Isao Takahata
10.          Hayao Miyazaki
11.         Hiroyuki Morita
12.          Hayao Miyazaki
13.           Gorō Miyazaki
14.          Hayao Miyazaki
15.    Hiromasa Yonebayashi
16.           Gorō Miyazaki
17.          Hayao Miyazaki
18.           Isao Takahata
19.    Hiromasa Yonebayashi
```

```
df.director.value_counts()
```

```
Hayao Miyazaki          9
Isao Takahata           5
Gorō Miyazaki           2
Hiromasa Yonebayashi    2
Hiroyuki Morita         1
Yoshifumi Kondō         1
Name: director, dtype: int64
```

Vemos que el director 'Hayao Miyazaki' estuvo presente en 9 films, veamos cuales fueron

```
df[df.director == "Hayao Miyazaki"]
```

| title  | director| 
| ------------- | ------------- | 
| Castle in the Sky  | Hayao Miyazaki  | 
| My Neighbor Totoro  | Hayao Miyazaki  | 
| Kiki's Delivery Service  | Hayao Miyazaki  | 
| Porco Rosso  | Hayao Miyazaki  | 
| Princess Mononoke  | Hayao Miyazaki  | 
| Spirited Away  | Hayao Miyazaki  | 
| Howl's Moving Castle  | Hayao Miyazaki  | 
| Ponyo  | Hayao Miyazaki   | 
| The Wind Rises  | Hayao Miyazaki  | 

Visualizaremos en una gráfica en de pastel como fue la distribuición de los directores

```
df.director.value_counts().plot(kind="pie")
```

![](https://raw.githubusercontent.com/DevPhantomUNAM/Proyecto_Visualizacion-De-Datos-Desde-API-Ghilbli-Con-Python/main/assets/img/gra1.jpg)

### 4.2.2 Evaluaremos la calificación que obtuvo cada film
Como los valores de rt_score los tenemos en string, los pasaremos a una nueva columan transformada en entero cada elemento

```
df["rt_scoreINT"] = ""
```
```
valores = df.rt_score.astype(int)
```

```
valores
```
```
0      95
1      97
2      93
3      96
4     100
5      94
6      78
7      91
8      92
9      75
10     97
11     89
12     87
13     41
14     92
15     95
16     83
17     89
18    100
19     92
```

```
df["rt_scoreINT"] = valores
```
```
df.head()
```

| title  | director | rt_scoreINT  | 
| ------------- | ------------- | ------------- | 
| Castle in the Sky  | Hayao Miyazaki  | 95  | 
| Grave of the Fireflies  | Isao Takahata	  |97  | 
| My Neighbor Totoro  | Content Cell  | Content Cell  | 
| Kiki's Delivery Service  | Hayao Miyazaki  | 93  | 
| Only Yesterday  | Hayao Miyazaki  | 96  |
| Content Cell  | Isao Takahata  | 100  |

Ya tenemos una columna con los datos de rt_score trasnformados a entero
```
df.rt_scoreINT.sort_values()
```
13     41
9      75
6      78
16     83
12     87
17     89
11     89
7      91
14     92
19     92
8      92
2      93
5      94
15     95
0      95
3      96
10     97
1      97
4     100
18    100

```
df.rt_scoreINT.sort_values().value_counts()
```
92     3
95     2
89     2
100    2
97     2
94     1
93     1
91     1
87     1

```
df.rt_scoreINT.sort_values().value_counts().plot(kind="pie")
```
![](https://raw.githubusercontent.com/DevPhantomUNAM/Proyecto_Visualizacion-De-Datos-Desde-API-Ghilbli-Con-Python/main/assets/img/gra2.jpg)

### 4.3 People 

```
len(people)
```
```
43
```
Tenemos que contamos con 43 personajes (no son todos)
```
for i in people:
    print(i['name'])
```

* Pazu
* Lusheeta Toel Ul Laputa
* Dola
* Romska Palo Ul Laputa
* Uncle Pom
* General Muoro
* Duffi
* Louis
* Charles
* Henri
* Motro
* Okami
* Ashitaka
* San
* Eboshi
* Jigo
* Kohroku
* Gonza
* Hii-sama
* Yakul
* Shishigami
* Moro
* Jiji
* Satsuki Kusakabe
* Mei Kusakabe
* Tatsuo Kusakabe
* Yasuko Kusakabe
* Granny
* Kanta Ogaki
* Totoro
* Chu Totoro
* Chibi Totoro
* Catbus
* Niya
* Renaldo Moon aka Moon aka Muta
* Cat King
* Yuki
* Haru
* Baron Humbert von Gikkingen
* Natori
* Colonel Muska
* Porco Rosso
* Sosuke

```
peopledf = pd.DataFrame(people)
peopledf
```

| name | gender|
| ------------- | ------------- |
| Porco Rosso  | Male |
| Baron Humbert von Gikkingen  | Male	  |
| Totoro  | NA	 |
| Cat King  | Male	  |

Para optener los personajes con genero 'Female' hacemos una evaluación

```
len(peopledf[peopledf.gender == "Female" ])
```
```
13
```

```
peopledf.gender.value_counts()
```

```
Male      27
Female    13
NA         3
```

![](https://raw.githubusercontent.com/DevPhantomUNAM/Proyecto_Visualizacion-De-Datos-Desde-API-Ghilbli-Con-Python/main/assets/img/gra3.jpg)

### 4.4 Las mejores 5 películas de studio Ghilbli

Ahora que sabemos los films más polulares y los personajes, podemos sacar los personajes de estas películas.

```
df[df.rt_scoreINT > 95].title
```
1.              Grave of the Fireflies
3.             Kiki's Delivery Service
4.                      Only Yesterday
10.                      Spirited Away
18.    The Tale of the Princess Kaguya

### 4.5 Location

```
locationdf = pd.DataFrame(location)
locationdf.head()
```

| name  | terrain |
| ------------- | ------------- |
| Irontown	  | Mountain	  |
| Gutiokipanja	  | Hill  |
| The Cat Kingdom  | Plain	  |
| The Marsh House	  | Marsh  |

### 4.6 Species

```
speciesdf = pd.DataFrame(species)
speciesdf
```

| name  | 
| ------------- | 
| Human	  | 
| Totoro	|	  
| Spirit	  | 
| Cat		  |


