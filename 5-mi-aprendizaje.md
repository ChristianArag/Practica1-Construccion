## CHRISTIAN ARAGON

## CONSTRUCCION DE SOFTWARE GR1

## 1. Gestión de Imágenes y Descarga

| Tarea | Comando Clave | Concepto Reforzado |
| :--- | :--- | :--- |
| **Descargar Versión Específica** | `docker pull <imagen>:<tag>` | Siempre se debe especificar el **tag** (ej: `:alpine`). |
| **Identificador Único** | N/A | Las imágenes se identifican por un **Digest SHA-256**. |
| **Eliminar Imagen** | `docker rmi -f <imagen>` | Usar el flag **`-f`** para forzar la eliminación si hay contenedores usándola. |

---

## 2. Ciclo de Vida del Contenedor

| Tarea | Comando Clave | Flag Esencial | Propósito |
| :--- | :--- | :--- | :--- |
| **Crear (sin iniciar)** | `docker create --name <nombre> <imagen>` | N/A | Crea el contenedor sin ejecutar el proceso principal. |
| **Ejecutar en Segundo Plano** | `docker run -d --name <nombre> <imagen>` | **`-d` (detach)** | **Fundamental** para liberar la terminal y que el contenedor siga corriendo. |
| **Listar Todos** | `docker ps -a` | **`-a` (all)** | Muestra los contenedores **activos y detenidos**. |
| **Eliminar Forzada** | `docker rm -f <nombre>` | **`-f` (force)** | Necesario para eliminar contenedores que están **en ejecución**. |

---

## 3. Mapeo de Puertos y Servicios (Networking) 

El mapeo de puertos debe hacerse en el comando `docker run`.

| Tarea | Comando Clave | Sintaxis | Ejemplo Práctico |
| :--- | :--- | :--- | :--- |
| **Mapear un Solo Puerto** | `docker run -p` | `-p <host>:<contenedor>` | `docker run -d -p 3000:80 nginx:alpine` |
| **Mapear Múltiples Puertos** | `docker run -p -p` | Repetir `-p` para cada par de puertos. | `docker run -d -p 8080:8080 -p 50000:50000 jenkins/...` |
| **Publicar Todos** | `docker run -P` | **`-P` (uppercase)** | Asigna puertos aleatorios del host a todos los puertos expuestos del contenedor. |

---

## 4. Operaciones Interactivas (`docker exec`) 

| Tarea | Comando Clave | Flags Críticos | Propósito y Uso |
| :--- | :--- | :--- | :--- |
| **Shell Interactivo** | `docker exec <nombre> <shell>` | **`-it`** | **Esencial** para abrir una terminal funcional (bidireccional). Usado para obtener la contraseña inicial de Jenkins. |
| **Ejemplo de Acceso** | `docker exec -it jenkins-server bash` | | Permite ejecutar comandos como `cat /ruta/del/archivo` dentro del contenedor. |
## Lo que Casi Falla en mi Docker

### 1. El Conflicto de Puertos 

* **El Problema:** Intentas usar un puerto en , pero otra aplicación ya lo está usando. Docker no puede compartirlo, así que falla.
* **La Solución:** Cambia el número del puerto de tu PC al iniciar el contenedor. Ejemplo: Usa `-p 8888:80` en lugar de `-p 8080:80` si el `8080` está ocupado.

### 2. El Contenedor se Apaga al Cerrar la Terminal 

* **El Problema:** Ejecutaste el comando `docker run` sin el *flag* de "segundo plano" (`-d`). Cuando cierras la terminal o presionas Ctrl+C, Docker piensa que quieres apagar la aplicación.
* **La Solución:** **Siempre** usa el *flag* **`-d`** (de *detach*) si quieres que el contenedor siga funcionando cuando dejes de mirarlo.

### 3. La Consola No Funciona Bien (`docker exec`) 

* **El Problema:** Quieres una consola funcional para escribir comandos, pero usaste solo `-i`. Te falta la "T" de terminal.
* **La Solución:** **Siempre** usa la combinación **`-it`** para abrir una sesión interactiva: `docker exec -it <nombre> bash`.

### 4. La Etiqueta (Tag) Incorrecta 

* **El Problema:** Te equivocaste al escribir la versión de la imagen (el *tag*) o asumiste que existía la versión `:latest`.
* **La Solución:** **Revisa y copia** el *tag* exacto desde Docker Hub (ej: `rabbitmq:3.10-management-alpine`). Un error en un número o guion causa el fallo.

### 5. El Contenedor no se Borra 

* **El Problema:** Docker te dice que no puedes eliminar el contenedor porque está "en uso" (es decir, **está corriendo**).
* **La Solución:** Si estás seguro de que lo quieres eliminar, usa el **borrado forzado** con `-f`: `docker rm -f <nombre-contenedor>`.

### 6. El Problema del `bash` vs. `sh` 

* **El Problema:** Intentas acceder con `bash` (`docker exec -it ... bash`), pero en contenedores muy pequeños (como los que usan **Alpine Linux**), el *shell* es más simple, llamado **`sh`**.
* **La Solución:** Si `bash` falla, intenta con **`sh`**: `docker exec -it <nombre> sh`.
