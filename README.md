# MataNotas
Aplicación de notas simple y fácil de usar, desarrollada con Cordova para fines educativos. Permite crear, editar, borrar y guardar notas, así como agregar imágenes y ubicaciones geográficas. Un proyecto ideal para aprender los fundamentos del desarrollo móvil.

###### Dentro de la carpeta Notas se puede encontrar documentacion mas explicita sobre el proyecto

# Comandos  
- compilar:
    ~~~
    cordova build android
    ~~~
- Probar en android:
    ~~~
    cordova run android
    ~~~
- Probar en Browser:
    ~~~
    cordova run browser
    ~~~

## Clase 1  
### Requisitos previos
- Sistema operativo: Windows, macOS o Linux.  
- Conexión a internet: Para descargar los instaladores.
### 1. Instalación de Node.js
- Descarga [Node.js](ttps://nodejs.org/)  
- Ejecuta el instalador y sigue las instrucciones.
### 2. Instalación de Cordova
- Abre una terminal o línea de comandos.  
  - Ejecuta el siguiente comando:  
    ~~~
    npm install -g cordova  
    ~~~
### 3. Configuración del JDK (Java Development Kit)
- Descarga: Descarga el JDK 18.0.2.1 desde el sitio web de Oracle.  
- Sigue las instrucciones del instalador para colocar el JDK en la carpeta C:\Program Files.  
  - Configuración de variables de entorno:  
    - Abre el *Panel de control* -> *Sistema y seguridad* -> *Sistema* -> *Configuración avanzada del sistema* -> *Variables de entorno*  
    - En **"Variables del sistema"** crea una nueva variable:  
            Nombre: JAVA_HOME  
            Valor: La ruta hasta la carpeta del JDK (por ejemplo, C:\Program Files\Java\jdk-18.0.2.1)  
    - Edita la variable "Path" y agrega las siguientes rutas:
%JAVA_HOME%\bin
%JAVA_HOME%\jre\bin  
### 4. Configuración de Gradle
- Descarga: Descarga Gradle 8.7 y colócalo en C:\Program Files  
- Configuración de variables de entorno:  
    - Crea una nueva variable:  
Nombre: GRADLE_HOME
Valor: La ruta hasta la carpeta de Gradle (por ejemplo, C:\Program Files\gradle-8.7)
    - Edita la variable "Path" y agrega la ruta: %GRADLE_HOME%\bin  
### 5. Instalación de Android Studio y SDK
- Descarga e instalación: Descarga [Android Studio](https://developer.android.com/studio) y sigue las instrucciones de instalación.  
- Configuración del SDK:
    - Abre Android Studio y configura el SDK para incluir al menos las siguientes versiones:
        - Android 13 (Tiramisu)
        - Android 14 (API level 34)
        - Android API 35.
    - Instala las herramientas necesarias como Android SDK Build Tools, Android SDK Platform-tools, Android Emulator, etc.
    - Configuración de variables de entorno:
        - Crea una nueva variable:
Nombre: ANDROID_HOME  
Valor: La ruta hasta la carpeta del SDK (por ejemplo, C:\Users\tu_usuario\AppData\Local\Android\Sdk)
        - Edita la variable "Path" y agrega las siguientes rutas:
%ANDROID_HOME%\platform-tools  
%ANDROID_HOME%\tools  
%ANDROID_HOME%\build-tools  
%ANDROID_HOME%\emulator  
%ANDROID_HOME%\cmdline-tools  
%ANDROID_HOME%\build-tools\34.0.0  
### 6. Creación de tu primer proyecto Cordova  
- Abre una terminal o línea de comandos.
- Navega hasta la carpeta donde deseas crear tu proyecto.
- Ejecuta el siguiente comando:  
~~~
cordova create mi_proyecto com.ejemplo.mi_proyecto MiProyecto
~~~

> mi_proyecto: Nombre de la carpeta del proyecto.  
com.ejemplo.mi_proyecto: Identificador único del proyecto.
MiProyecto: Nombre de la aplicación.  

- Agrega las plataformas:
~~~
cordova platform add android
~~~
~~~
cordova platform add browser
~~~

- Construye la aplicación:
~~~
cordova build android
~~~

***Recursos Adicionales***

> Documentación de [Cordova](https://cordova.apache.org/docs/en/latest/)  
Foros de Cordova: Busca en foros como Stack Overflow para resolver dudas.  


### 7. hacemos un bosquejo general de la aplicacion  
- Borramos todos los comentarios que nos deja Apache Cordova.  
- Quitamos todo lo que encontramos en **index.js**.
- Quitamos todo lo que esta en **index.css**.
- Quitamos todo lo que esta dentro de la etiqueta **<body>** en **index.html**.
- agregamos `bootstrap` y `fontAweson` al proyecto.
- Dentro del **<body>** en **index.html** creamos un contenedor donde dibujaremos lo que serian nuestras notas, ademas del boton desde el cual posteriormente estaremos agregando las notas.  
#### Nota
> Cuando se este llamando al `bootstrap`, al `fontAweson` y a nuestras propias librerias, hay que tener en cuenta el orden en que se llaman, porque lo ultimo que se llame, va a ser lo qe tendra mas relevancia sobre los demas (*sobretodo en los estilos*)  
___  
## Clase 2  
#### Objetivos:

- Implementar la funcionalidad de agregar notas.
- Introducir la programación orientada a objetos.

#### Contenido:

### 1. Solución al problema del texto largo:

Se agregó el estilo `overflow-y: auto; overflow-x: hidden;` a la clase .card para permitir el desplazamiento vertical y evitar que el texto se salga de los límites.
### 2. Creación del modal:

Se creó un modal utilizando Bootstrap para permitir a los usuarios agregar nuevas notas.  
El modal contiene un formulario con campos para el título y el contenido de la nota.
### 3. Almacenamiento de notas:

Se utilizó **localStorage** para persistir las notas entre sesiones del navegador.
Las notas se almacenan en un array y se serializan como JSON antes de guardarlas en localStorage.
### 4. Visualización de notas:

Se creó una función para iterar sobre el array de notas y renderizarlas en la página en forma de tarjetas.
### 5. Introducción a la programación orientada a objetos:

Se creó una clase Nota para representar cada nota, encapsulando sus propiedades (título y contenido) y métodos (guardar, eliminar, editar).
Se modificó el código existente para utilizar la clase Nota, mejorando la organización y mantenibilidad del código.
#### Ventajas de la programación orientada a objetos:

- Organización: Agrupa datos y comportamiento relacionados en objetos.
- Reutilización: Permite crear múltiples objetos a partir de una misma clase.
- Mantenibilidad: Facilita la modificación y ampliación del código.
- Abstracción: Oculta la complejidad interna de los objetos.
### 6. Próximos pasos:

- Implementar los métodos de la clase Nota (eliminar, editar).
- Auro seleccionar el titulo al empezar a agregar la nota.  

___

# Clase 3
#### Objetivo:

- Implementar la funcionalidad de enfocar automáticamente el campo de título al abrir el modal para agregar una nueva nota.
- Permitir editar notas existentes directamente en el modal.
- Agregar la funcionalidad de eliminar notas.
- Agregar la funcionabilidad de buscar notas.
- Agregar la funcionalidad de agregar imágenes a las notas.
- Mejorar la interfaz de usuario con un menú de opciones en el modal.

### 1. Enfocando el campo de título:

Se agregó un evento onclick al botón que abre el modal para llamar un setTimeout() para asegurar que el campo de título reciba el foco después de que el modal se haya abierto completamente.
### 2. Editando notas:

- Se agregó un botón "Editar" al modal, inicialmente oculto.
    - Al hacer clic en una nota, el botón "Editar" se muestra y los campos del formulario se rellenan con los datos de la nota seleccionada.
- Se implementó un evento onclick en el botón "Editar" para guardar los cambios realizados.
- Se utilizó el índice de la nota en el array para identificar la nota a editar y actualizar sus datos.
### 3. Eliminando notas:

- Se agregó un botón "Eliminar" al modal.
    - Al hacer clic en el botón "Eliminar", se elimina la nota seleccionada del array y se actualiza el localStorage.
#### Puntos Clave:

>Uso de setTimeout(): Para asegurar que el campo de título reciba el foco después de que el modal se haya abierto.
Manejo de eventos: Se utilizaron eventos onclick para activar las diferentes funcionalidades del modal.
Manipulación del DOM: Se modificó el DOM para mostrar y ocultar elementos según sea necesario.
Manejo de arrays: Se utilizó el método splice() para eliminar elementos de un array.
### 4. Buscar Nota:
- Agregar un campo de búsqueda:

    - Se crea un input de texto con un icono de lupa para realizar las búsquedas.
    - Se asigna el evento input a este campo para detectar cada cambio en tiempo real.
- Crear la función buscarNota():

    - Obtener el texto a buscar: Se extrae el valor del input de búsqueda y se elimina cualquier espacio en blanco al principio y al final.
    - Filtrar las notas: Se utiliza el método filter() de los arrays para crear un nuevo array con las notas que coincidan con el texto de búsqueda. La coincidencia se realiza comparando el texto de búsqueda (convertido a minúsculas) con el título y el contenido de cada nota (también convertidos a minúsculas).
    - Mostrar los resultados: Se llama a la función mostrarNotas() pasando el array de notas filtradas como parámetro.
- Mostrar un mensaje si no hay resultados:

    - Se agrega un condicional para verificar si el array de notas filtradas está vacío.
        - Si está vacío, se muestra un mensaje indicando que no se encontraron resultados.
- Agregar un botón para cancelar la búsqueda:

    - Se agrega un botón de cierre con su respectivo método para limpiar el campo de búsqueda y mostrar todas las notas.
#### Detalles adicionales:
>**Eficiencia:** Se utiliza el método toLowerCase() para realizar comparaciones sin distinción entre mayúsculas y minúsculas, lo que mejora la eficiencia de la búsqueda.
**Experiencia de usuario:** Se agrega un mensaje claro cuando no se encuentran resultados.
**Flexibilidad:** El código es modular y puede adaptarse fácilmente a futuras modificaciones.  

### 5. Reestructuracion de las clases:

- Se agregaron propiedades para almacenar referencias a elementos del DOM como el contenedor de imágenes y el modal.
- Se crearon métodos para manejar la toma de fotos, agregar imágenes a las notas, eliminar imágenes y mostrar las imágenes en las notas y en el modal.
### 6. Mejora de la Interfaz

- Se agregó un botón de cámara en el menú de opciones del modal para tomar fotos.
- Se agregó un contenedor para mostrar las imágenes en el modal.
- Se implementó un mecanismo para eliminar imágenes individuales.
### 7. Funcionalidad:

- Se utiliza el plugin `cordova-plugin-camera` para tomar fotos.
- Se utiliza el plugin `cordova-plugin-file@8.1.0` para manejar las rutas de las imágenes.
    - Las imágenes se almacenan como URLs en el objeto de la nota.
Se muestra un mensaje de error si se produce algún error al tomar la foto.
- Se ha mejorado la experiencia de usuario al permitir editar las imágenes directamente en el modal.
#### Principales mejoras:

> **Mayor funcionalidad:** La aplicación ahora permite agregar imágenes a las notas, enriqueciendo su contenido.
**Mejor interfaz de usuario:** El menú de opciones en el modal facilita la gestión de las notas y las imágenes.
**Mayor flexibilidad:** La estructura del código se ha mejorado para permitir futuras ampliaciones.
___