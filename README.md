# TALLER DE DE MODULARIZACIÓN CON VIRTUALIZACIÓN E INTRODUCCIÓN A DOCKER

En este  taller se creó una aplicación web usando el micro-framework de Spark java, la aplicación web ofrece las siguientes funciones: Seno, Coseno, Palíndromo, Vector. Una vez implementada esta aplicación se procede a construir un container docker, desplegarlo y configurarlo en nuestra máquina local. Luego, creamos un repositorio en DockerHub y subiremos la imagen al repositorio.

## Diseño de la aplicación

La aplicación está diseñada para cumplir con los requisitos especificados en el enunciado del taller y proporcionar una experiencia de usuario fluida y satisfactoria. A continuación, se describen los principales componentes y características de la aplicación:

- La clase `SparkWebServer` define un servidor web Java utilizando el framework Spark, configurando rutas para manejar solicitudes HTTP GET en diferentes endpoints. Inicia el servidor en un puerto específico, y establece la ubicación de los archivos estáticos en el directorio `/public`. Además, implementa endpoints para calcular funciones trigonométricas, verificar palíndromos y calcular la distancia entre dos puntos en un plano cartesiano, extrayendo parámetros de las solicitudes HTTP.
- Se creó un contenedor Docker que encapsula la aplicación `SparkWebServer`, lo que facilita su despliegue y ejecución en diferentes entornos de manera consistente. Este contenedor se configuró para incluir todas las dependencias necesarias y se definió un archivo `Dockerfile` para construirlo adecuadamente. 

## Extensión de la aplicación.

- Se podrían implmentar características adicionales como soporte para otros métodos HTTP.

## Guía de Inicio

Las siguientes instrucciones le permitirán descargar una copia y ejecutar la aplicación en su máquina local.

### Prerrequisitos

- Java versión 8 OpenJDK
- Docker
- Maven
- Git

## Instalación 

### Docker

1. Abra la aplicación de escritorio de Docker.
![image](https://github.com/user-attachments/assets/26894d1c-9ba6-41ba-aaaf-3ffc8049556e)


2. Ejecute el siguiente comando para descargar la imagen del repositorio de docker:
   
     ```
      docker run -d -p 34000:46000 --name unruffled_blackburn dockersparkprimer
     ```

   Debería ver algo así en consola:

<img width="1873" height="62" alt="image" src="https://github.com/user-attachments/assets/fd5cd92f-8697-44d3-93e2-f50142d4cb67" />


3. creamos los otros 2 contenedores 
     ```
      docker run -d -p 34001:46000 --name unruffled_blackburn1 dockersparkprimer
     ```


     ```
      docker run -d -p 34002:46000 --name unruffled_blackburn2 dockersparkprimer
     ```

   Verifique en la aplicación de escritorio de Docker que el contenedor se esté ejecutando
   
   <img width="1917" height="744" alt="image" src="https://github.com/user-attachments/assets/9bbcee00-1cd5-4e4e-aefb-6081db5c87c8" />

### Aplicación corriendo correctamente

- 34000
  <img width="1428" height="990" alt="image" src="https://github.com/user-attachments/assets/0945a4e6-72b3-4854-a5b5-f11e04ca0622" />

- 34001
  <img width="1541" height="978" alt="image" src="https://github.com/user-attachments/assets/f7f14394-ee3c-436f-b8f0-222552bcdb31" />

- 34002
<img width="1584" height="961" alt="image" src="https://github.com/user-attachments/assets/97eae1ae-b07e-4f88-ae58-bc45dd25b3f3" />

### Repositorio en GitHub

1. Ubíquese sobre el directorio donde desea realizar la descarga y ejecute el siguiente comando:
   
     ``` 
     git clone https://github.com/juliandtrianar/lab4-AREP.git
      ```

2. Navegue al directorio del proyecto:
   
      ``` 
      cd taller4
      ```

3. Ejecute el siguiente comando para compilar el código:

      ``` 
      mvn compile 
      ```

5.  Ejecute el siguiente comando para empaquetar el proyecto:
   
      ```
      
      mvn package 
      ``` 

6. Para iniciar el servidor, ejecute el siguiente comando:

    ```
    java -cp "target/classes;target/dependency/*" org.eci.arep.app.SparkWebServer 
    ```

7. Verifique en la linea de comandos que se está ejecutando la aplicación:

<img width="1904" height="405" alt="image" src="https://github.com/user-attachments/assets/88cc7fb5-39d8-4a23-827a-a8626d3cc493" />



   
## Probando la Aplicación.  

Ingrese a la siguiente URL para ingresar a el cliente: `http://localhost:34000/index.html`.
Si está ejecutando la aplicación desde la máquina virtual de java y no con el contenedor, el puerto es el `4567`.

Ingrese en los campos del formulario los valores, de clic en el botón `Search`:
<img width="1435" height="902" alt="image" src="https://github.com/user-attachments/assets/85242ed2-3914-4857-8935-65d1cfbc82c0" />




- Para las funciones Seno y Coseno ingresé el valor que desea calcular en radianes.
- Para la función palíndromo ingrese la palabra que quiere evaluar, si la palabra es palíndromo retornará true,  de lo contrario retornará false.
- Para la función Vector, ingrese las coordenadas de los puntos en el formato **x,y**

![image](https://github.com/user-attachments/assets/79ad8731-9bdb-46fb-88ab-98f4d5c9ea7b)

## Despliegue en AWS con EC2
1. Crear una instancia EC2
   <img width="1601" height="395" alt="image" src="https://github.com/user-attachments/assets/85296162-346c-4552-adeb-b46140e9be96" />


2. Configurar el puerto en el grupo de seguridad.
<img width="1540" height="329" alt="image" src="https://github.com/user-attachments/assets/aa012114-be30-4cc7-97f0-a5e36916badd" />


3. conectarse vía SSH.
   <img width="862" height="289" alt="image" src="https://github.com/user-attachments/assets/3ff30519-f673-4c5e-a283-47b228b40be0" />

4. Transferimos las imagenes a la instancia

   sudo docker run -d -p 46000:35000 -e DOCKER_ENV=true --name dockercontaineraws juliandtrianar/juliandtrianar-lab4
   
6. Abrimos el link del despliegue
   <img width="1726" height="957" alt="image" src="https://github.com/user-attachments/assets/35076528-d5ed-4774-b00f-ff8b6af8a776" />


   ### Video


## Autor

- Julián David Triana Roa

## Construido con. 

- Maven - Administrador de dependencias

## Versión
1.0.0
