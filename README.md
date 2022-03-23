# Nginx-docker Lapini Alessandro y Serra Josep

# Primero de todo nos instalamos el docker de nginx de dockerhub

![nginx](img/dockerhub.PNG)

## Arrancamos el contenedor 

``` 
docker run --rm -d -p 8080:80 --name web nginx 
```

![nginxweb](img/nginxweb.PNG)

# Agregar HTML personalizado

Creamos un repositorio donde se encontrará nuestro html que utilizará nuestra web.

![path](img/ruta.PNG)

En index.html metemos:

```
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>Docker Nginx</title>
</head>
<body>
  <h2>Hello desde Cibeseguridad</h2>
</body>
</html>
```

Y ejecutamos el siguiente comando que montara nuestro directorio local en el contenedor en ejecucuión en **/usr/share/nginx/html**
```
docker run --rm -d -p 8080:80 --name web -v ~/Documentos/nginx/site-content:/usr/share/nginx/html nginx
```

# Crear una imagen personalizada 

Generamos un Dockerfile en el mismo repositorio y metemos el siguiente código:

![dockerfile](img/dockerfile.PNG)

```
FROM nginx:latest

COPY ./index.html /usr/share/nginx/html/index.html
```

Construimos nuestra imagen:

![dockerimage](img/dockerimage.PNG)

Ejecutamos nuestra imagen:

![exedocker](img/exedocker.PNG)

Demostración:

![¡page](img/apge.PNG)

# Parte B

creamos la maquina virtual de azure con debian, una vez configurada 
con docker:

Creamos un index-html:

![index](img/index.PNG)

realizamos el siguiente comando:

```
docker pull nginx:latest 
```

![nginx](img/nginxPNG.PNG)

Ejecutamos el contenedor con el index.html creado anterioirmente y con la imagen de nginx

![exec](img/exec.PNG)

Vamos a la maquina virtual creada / redes y añadimos el puerto 80:

![azure](img/azure.PNG)

Abrimos en el navegador con nuestra ip:

![ip](img/ip.PNG)
