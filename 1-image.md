# Imagen
### Descargar imagen
Descarga la última versión de la imagen disponible en el registro de Docker.

```
docker pull <nombre imagen> 
```

Descarga una versión específica de la imagen, cada imagen tiene etiquetas (tags) para diferentes versiones.
Una imagen puede tener la etiqueta latest para representar la última versión, si no se especifica una etiqueta se hará referencia a la versión latest.

```
docker pull <nombre imagen>:<tag>
```

Descargar la imagen **hello-world**
# COMPLETAR

**¿Qué es nginx**

Es un servidor web/proxy inverso de código abierto y alto rendimiento, conocido por su eficiencia y bajo consumo de recursos, especialmente al manejar muchas conexiones concurrentes.

# COMPLETAR 

Descargar la imagen  **nginx** en la versión **alpine**

```
docker pull nginx:alpine
```


# COMPLETAR

### Listar imágenes

```
docker images
```
<img width="517" height="81" alt="image" src="https://github.com/user-attachments/assets/b39dd182-37cb-4304-9e3a-aec300bd0013" />



# COLOCAR UNA CAPTURA DE PANTALLA DEL RESULTADO 

**Identificadores**

En Docker, se utilizan varios identificadores para diferenciar de manera única los elementos del sistema, como imágenes, contenedores, volúmenes y redes. Estos identificadores son generados automáticamente por Docker y son únicos dentro del contexto del sistema Docker en el que se encuentran. 

### Inspeccionar una imagen
El comando docker inspect se utiliza para obtener información detallada sobre un objeto de Docker específico, como un contenedor, una imagen, un volumen o una red.  Proporciona información en formato JSON sobre el objeto especificado.

```
docker inspect <nombre imagen>
docker inspect <nombre imagen>:<tag>
```

Inspeccionar la imagen hello-world 

<img width="1055" height="840" alt="image" src="https://github.com/user-attachments/assets/f9b8c90c-3844-41e2-81a7-36b0a13aea73" />

# COMPLETAR

**¿Con qué algoritmo se está generando el ID de la imagen**

sha256

# COMPLETAR

### Filtrar imágenes

```
docker images | grep <termino a buscar>

```
<img width="484" height="48" alt="image" src="https://github.com/user-attachments/assets/b43005f0-41f3-46d5-b2e7-d2fe46c92f78" />


### Para eliminar una imagen
Eliminar permanentemente la imagen de tu sistema Docker.

```
docker rmi <nombre imagen>:<tag>
```

Eliminar la imagen hello-world 
# COMPLETAR

-f: Es la opción para forzar la eliminación de la imagen incluso si hay contenedores en ejecución que utilizan esa imagen.
Cuando eliminas una imagen Docker, Docker no elimina automáticamente los contenedores que se han creado a partir de esa imagen. Esto significa que, aunque hayas eliminado la imagen, el contenedor seguirá ejecutándose normalmente.  
**Considerar**
Eliminar una imagen no afecta a los contenedores que se han creado a partir de esa imagen, a menos que esos contenedores dependan de archivos o configuraciones específicas de la imagen eliminada. En ese caso, es posible que los contenedores se comporten de manera inesperada después de eliminar la imagen.
Es una buena práctica detener y eliminar todos los contenedores que dependan de una imagen antes de eliminar la imagen en sí.

```
docker rmi -f <nombre imagen>:<tag>
```
<img width="756" height="237" alt="image" src="https://github.com/user-attachments/assets/e5b41a21-c4d0-4c9f-805d-5ea7fee469b1" />
