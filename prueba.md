sudo systemctl start docker
sudo systemctl enable docker

# Resolución de ejercicios EGC

## Ejercicio A

#### 1. Realice un fork de este repositorio con el nombre EGC-1730-"uvus".

#### Ir al repo y pulsar en Fork.

#### 2. Clone el repositorio del cual ha hecho el fork. :camera:

#### ```git clone git@github.com:USUARIO/REPOSITORIO.git```

#### 3. Cree una nueva rama llamada desarrollo en el repositorio. :camera:

#### ```git checkout -b desarrollo```

#### 4. "Salte" a la rama recién creada. :camera:

#### ```git checkout desarrollo```

#### 5. En el código de DECIDE del repositorio existe un error. Identifique el error

#### ejecutando en su máquina el código.

#### Suerte lusi

#### 6. Cree una "issue" en el fork del repositorio para reportar el error según lo visto en

#### clase. :camera:

#### Si no salen las Issues, activarlas en nuestro fork, Settings.

#### Creamos la issue, y hay de distintos tipos:

##### ▪ bug: La incidencia describe un fallo de programación en el software.

##### ▪ duplicate: Ya existe otra incidencia que describe los mismo que esta.

##### ▪ enhancement: Una solicitud de mejora en el software.

##### ▪ good first issue: Esta incidencia es idonea para un desarrollador del equipo junior, o con menor experiencia en el software.

##### ▪ help wanted: Esta incidencia describe una petición de ayuda.

##### ▪ invalid: Esta incidencia es incorrecta, refleja una petición que no tiene sentido.

##### ▪ question: Esta incidencia describe una pregunta a responder para el equipo de desarrollo.

##### ▪ wontfix: Esta incidencia no tiene solución posible. Se emplea cuando se describe como incidencia un comportamiento que parece ser defectuoso, pero que en
##### realidad es una funcionalidad. También se puede emplear para una incidencia que describe un problema, para la que no existe solución posible. Hay que tener ##### una buena razón para etiquetar una incidencia de esta manera.

#### 7. Realice las modificaciones necesarias para corregir el error.

#### Todo son risas hasta que te piden esto

#### 8. Haga commit de los cambios en la rama de desarrollo. :camera:
    ```git add lo que sea```
    ```git commit -m “Mensajito”```
#### 9. Cree un archivo travis.yml para pasar las pruebas exclusivamente del modulo del modulo
store.
    El travis de siempre pero en script le ponemos:
    ```python manage.py test store```
#### 10. Haga commit el archivo travis.yml
    ```git add .travis.yml```
    ```git commit -m “travis.yml”```
#### 11. Refleje los cambios del repositorio en el repositorio remoto que creó en el primer
paso. :camera:
    ```git push origin desarrollo```


## Ejercicio B

#### 1. Prepare travis para que ejecute los tests cuando se realice algún cambio en la rama
master.:camera:

2. Salte a la rama master del repositorio.
    ```git checkout master```
3. Cree un archivo travis.yml para pasar las todas las pruebas de decide. :camera:
    El travis de siempre pero en la rama master
4. Haga commit de los cambios realizados.:camera:
    ```git add```
    ```git commit```
5. Haga merge de la rama de desarrollo con la rama master del repositorio y asocielo a la
issue del Ejercicio A.:camera:
    Para asociar la issue con el merge, hacer el merge desde interfaz y ponerle el # con
    el numero de issue.
    // git merge desarrollo (estando en master)


## Ejercicio C

1. Realice los cambios necesarios en los archivos de docker para que despliegue este
repositorio. :camera:
En el Dockerfile (directorio docker) cambiar la URL de git por la de nuestro proyecto
2. Haga commit de los cambios realizados.:camera:
    ```git add “Dockerfile”```
    ```git commit “Dockerfile”```

## Ejercicio D

#### 1. Realice los cambios necesarios en los archivos de docker para solucionar el error

#### al desplegar la base de datos en la rama de desarrollo. :camera:

#### Coger el local_settings.travis.yml y cambiar el host ‘db’ por ‘localhost’.??

2. Configure y añada los archivos necesarios para desplegar DECIDE en Heroku cada
nueva versión subida al master del mismo.:camera:
**Credenciales:**
luciadelcarmenfuentes@gmail.com
LUCIAguapa
En heroku, dentro del proyecto ir a deploy, seleccionar github, elegir proyecto, y la rama.
3. En la rama master del repo hacer
```
heroku create “app-name”
heroku git:remote -a "app name"

En la raiz crear un archivo “Procfile” tal cual con esto:
release: sh -c 'cd decide && python manage.py migrate'
web: sh -c 'cd decide && gunicorn decide.wsgi --log-file -‘


En el requirements.txt añadir
django-heroku
gunicorn
```
#### decide/decide/settings.py
```
 BASEURL = 'https://TU URL’ (mirar en Heroku)

 APIS = {}

 ...

 import django_heroku

django_heroku.settings(locals())
```
#### ```git push heroku master```

### ```heroku run -a YOUR APP NAME "sh -c 'cd decide && python manage.py createsuperuser'"```



