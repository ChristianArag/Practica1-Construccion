# Contenedores

### Crear un contenedor
Para crear un nuevo contenedor Docker a partir de una imagen específica, pero sin iniciarlo automáticamente. 

```
docker create --name <nombre contenedor> <nombre imagen>:<tag>
```
Crear el contenedor  **srv-web** usando la imagen nginx version alpine

<img width="543" height="54" alt="image" src="https://github.com/user-attachments/assets/a8391b10-9e42-426d-bfc0-1ceca7df3850" />

# COMPLETAR

Si creas un contenedor en Docker sin asignarle un nombre específico utilizando la opción --name, Docker asignará automáticamente un nombre aleatorio al contenedor. Este nombre suele consistir en una combinación de palabras y números.  

Crear el contenedor usando la imagen hello-world

<img width="531" height="43" alt="image" src="https://github.com/user-attachments/assets/1065e7c7-5cf7-4c2d-98cb-1186bc0d33c7" />

# COMPLETAR

### Listar los contenedores ejecutándose o no

```
docker ps -a
```
<img width="1106" height="91" alt="image" src="https://github.com/user-attachments/assets/c50e3cbb-f148-4e83-a06c-e968f4601a48" />

### Para iniciar un contenedor

```
docker start <nombre contenedor o identificador>
```
Iniciar el contenedor srv-web 

<img width="321" height="46" alt="image" src="https://github.com/user-attachments/assets/e604f64e-b2de-404e-a555-9c96dfad2f8f" />

# COMPLETAR

### Listar los contenedores ejecutándose
```
docker ps 
docker ps | grep <nombre contenedor>
```

<img width="1024" height="62" alt="image" src="https://github.com/user-attachments/assets/57dac154-374e-4836-b7e6-e1476a1c7b5b" />

### Para detener un contenedor

```
docker stop <nombre contenedor>
```
<img width="583" height="126" alt="image" src="https://github.com/user-attachments/assets/41240f78-1904-49fc-b650-98c5da7c2397" />

### Para crear un contenedor y ejecutarlo inmediatamente

```
docker run --name <nombre contenedor> <nombre imagen>:<tag>
```
![Ecosistema de Docker](dockerRun.PNG)

Crear y ejecutar inmediatamente el contenedor **srv-web2** usando la imagen nginx:alpine

<img width="784" height="437" alt="image" src="https://github.com/user-attachments/assets/8badc785-e522-4523-9e1b-aa3b74292fe6" />

# COMPLETAR

**¿Qué sucede luego de la ejecución del comando?**

El contenedor se crea y se ejecuta

# COMPLETAR  

Cuando ejecutas un contenedor en primer plano sin la opción -d (modo detach), el contenedor captura la entrada estándar (stdin) del terminal, lo que significa que el terminal queda "atrapado" y no puedes introducir más comandos hasta que detengas el contenedor.

### Para crear un contenedor y ejecutarlo inmediatamente sin estar vinculados al mismo
-d: Es la opción que indica a Docker que ejecute el contenedor en segundo plano (en modo "detach").
Cuando un contenedor se ejecuta en segundo plano, Docker devuelve el control al terminal inmediatamente después de iniciar el contenedor, lo que permite al usuario seguir ejecutando otros comandos en el mismo terminal sin que el contenedor detenga la interacción.

```
docker run -d --name <nombre contenedor> <nombre imagen>:tag
```
Crear y ejecutar inmediatamente el contenedor **srv-web3** en modo detach usando la imagen nginx:alpine

<img width="862" height="116" alt="image" src="https://github.com/user-attachments/assets/0624989e-f4fd-497f-a24c-04e97960b6e6" />

# COMPLETAR

### Para eliminar un contenedor

```
docker rm <nombre contenedor>
```
Eliminar el contenedor que se creó a partir de la imagen hello-world 

<img width="374" height="42" alt="image" src="https://github.com/user-attachments/assets/dea8b45e-be7c-4cca-95ec-5d419c24cf8e" />


# COMPLETAR

Verificar que el contenedor que se eliminó

<img width="1055" height="111" alt="image" src="https://github.com/user-attachments/assets/c4d6b5ba-4b7d-4f81-8b24-3752dea0f94e" />

# COMPLETAR

### Para eliminar un contenedor que esté ejecutándose

```
docker rm -f <nombre contenedor>
```
Eliminar el contenedor **srv-web3** }
<img width="364" height="42" alt="image" src="https://github.com/user-attachments/assets/586d8d46-7ac7-43a2-b526-3d490e2af527" />

# COMPLETAR

Verificar que el contenedor que se eliminó

<img width="571" height="53" alt="image" src="https://github.com/user-attachments/assets/c7679768-0290-4962-9674-aa7f308dee7b" />

# COMPLETAR

### Para inspecionar un contenedor 

Inspeccionar el contenedor **srv-web** 
<img width="1505" height="760" alt="image" src="https://github.com/user-attachments/assets/01fa04cd-b6a7-4250-be17-d035a44505a3" />

# COMPLETAR
