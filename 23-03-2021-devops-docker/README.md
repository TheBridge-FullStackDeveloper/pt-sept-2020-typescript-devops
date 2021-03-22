# DOCKER 🐳

## Cheatsheet 📝

- Descargar una imagen de `docker-hub`
```js
  docker pull name:tag
```

- Ver todas las imágenes que Docker tiene almacenadas
```js
  docker images
```

- Ver todos los contenedores activos
```js
  docker ps [-a]
```
1. -a => all; muestra todos los contenedores, tanto los que están corriendo como los que están parados

- Ver consumo de memoria y red de los contenedores activos
```js
  docker stats
```

- Levantar un contenedor a partir de una imagen (sin opciones)
```js
  docker run `IMAGE_ID`
```

- Levantar un contenedor a partir de una imagen (con opciones)
```js
  docker run [-it] [--rm] [-d] [--name container-name] [-v host-path:container-path] [-w container-work-directory] [-p host-port:container-port] `IMAGE_ID` [command]
```
1. -it => interactivo; podrás interactuar con la salida del contenedor si fuera posible
2. --rm => eliminación; elimina el contenedor cuando termine de usarse
3. -d => detached; en lugar de ocupar la ventana de la terminal, el contenedor se ejecutará en segundo plano
4. --name => nombre; se le asigna un nombre al contenedor. Si no se especifica, se asignará uno por defecto
5. -v => volumen; se creará un directorio dentro del contenedor con todo el contenido que tenga la ruta host designada. Sirve para compartir un directorio entre el host y el contenedor. Teniendo en cuenta que la ruta host debe indicarse con una ruta absoluta. En entornos Linux eso se indica con `"$(pwd)"` y en Windows con `"%cd%"`
6. -w => directorio de trabajo; indica la ruta donde se lanzarán los comandos si hubiera alguno
7. -p => puertos; se realiza un mapeo entre el puerto del host (el que aparece en primer lugar) y el puerto del contenedor (el que aparece al final). Esto permite comunicación entre host y contenedor a través de los puertos designados. No confundir con `EXPOSE`
8. command => cualquier comando válido. Se lanzará desde la ruta del directorio de trabajo indicado antes. Aunque el comando lo escribamos y ejecutemos en nuestra consola, es el contenedor quien lo ejecuta sobre la ruta especificada y sobre los ficheros que haya en el volumen que hayamos creado

- Construir una imagen en base al fichero `dockerfile` en el directorio actual (ver fichero `dockerfile` y modificar lo necesario)
```js
  docker build -t image-tag .
```
1. -t => tag; es el nombre de la etiqueta de la imagen que vamos a construir. Poner como etiqueta `username/repo:image-tag` para poder subir la imagen al hub de Docker

- Subir una imagen a tu repo de `docker-hub`
```js
  docker push `username/repo:image-tag`
```

- Parar un contenedor
```js
  docker stop `CONTAINER_ID`
```

- Iniciar un contenedor parado
```js
  docker start `CONTAINER_ID`
```

- Reiniciar un contenedor
```js
  docker restart `CONTAINER_ID`
```

## Ejercicios ✨

Usando docker y la imagen `node:14.16-alpine3.10` crea una imagen diferente para cada ejercicio y súbela a tu repo de `docker-hub`. No puedes usar ni `npm` ni `node` instalados en tu ordenador ni `repl.it` ni ninguna herramienta web, límitate solo a lo que te da la imagen.

1. Haz la siguiente kata: https://www.codewars.com/kata/53368a47e38700bd8300030d
2. Haz la siguiente kata: https://www.codewars.com/kata/546f922b54af40e1e90001da

3. Haz un pequeño servidor con express que tenga dos rutas:
  - `/greet`: Debe devolver
  ```js
    {
      success: true,
      data: 'Hello!'
    }
  ```
  - `/pokemon/:pokemon`: Debe hacer una petición a la `Pokeapi` y devolver lo siguiente
  ```js
    {
      success: true,
      data: {
        name: 'nombre-pokemon',
        id: 'id-pokemon',
        pic: 'frontal-default-pic',
      }
    }
  ```

- Las dos siguientes katas son con `typescript`, investiga cómo puedes transpilar a la hora de trabajar solo con la imagen de node:
4. https://www.codewars.com/kata/515e271a311df0350d00000f
5. https://www.codewars.com/kata/54c27a33fb7da0db0100040e

A divertirse! 🚀 🌔 ✨
