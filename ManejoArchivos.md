
# Proyecto II

## Manejo de archivos en C++

El programa es un sistema básico de gestión de productos que permite al usuario
almacenar dentro de un archivo externo información de uno o varios productos la
cual podría visualizar y editar desde la ejecución de programa, dicho algoritmo le
permite realizar las siguientes operaciones proporcionando mensajes informativos
en caso de errores:

<a href="https://imgbb.com/"><img src="https://i.ibb.co/99s7mJ3/1.png" alt="1" border="0"></a>

- **Agregar Producto**:
  - Solicita al usuario ingresar un listado de información la cual esta compuesta por:
    código, nombre, precio, proveedor, existencia, estado (Aprobado/Reprobado) y
    descuento.
  - Verifica que el usuario no pueda ingresar dos productos con el mismo Código.
  - Verifica que no ingrese ningún valor negativo.
  - Por ultimo agrega la información dentro de un archivo "productos.txt" y muestra un
    mensaje de éxito y no contar con el archivo automáticamente lo crea.

<a href="https://imgbb.com/"><img src="https://i.ibb.co/7WsGz6Y/2.png" alt="2" border="0"></a>

- **Buscar Producto**:
  - Permite al usuario buscar un producto por código o nombre, o ya sea por una
    palabra lo cual permitirá observar todos los resultados relacionados.
  - Muestra los detalles del producto si se encuentra.
  - Informa si el producto no se encuentra en la base de datos.

<a href="https://imgbb.com/"><img src="https://i.ibb.co/MNs654R/3.png" alt="3" border="0"></a>

  <a href="https://imgbb.com/"><img src="https://i.ibb.co/7zB13Lc/4.png" alt="4" border="0"></a>

- **Modificar Producto**:
  - Permite que el usuario pueda modificar o cambiar todos los datos de un producto
    existente.
  - Solicita el código del producto a modificar, siendo Código el único atributo que no
    podrá modificar.
  - Guarda los cambios realizados dentro de el archivo "productos.txt" y muestra un
    mensaje de éxito.

<a href="https://imgbb.com/"><img src="https://i.ibb.co/7WYmBtT/5.png" alt="5" border="0"></a>

- **Salir del Programa**:
  - Permite al usuario salir del programa.
  - Almacenando toda la información ingresada en el programa dentro del archivo.

<a href="https://imgbb.com/"><img src="https://i.ibb.co/8Dzbcc8/6.png" alt="6" border="0"></a>
-

## Manual de Usuario:

- **Para la elaboración del programa se utilizaron las siguientes librerías:**
  Fue necesario la llamada de seis librerías para un buen desempeño del programa y pudiera ser más simple.

<a href="https://ibb.co/MgZCgHm"><img src="https://i.ibb.co/TwYgwGs/11.png" alt="11" border="0"></a>

- **Definición y declaración de la clase “producto”:**
  Se establece qué tipo de información podrá almacenar cada uno de los atributos, por ejemplo: valores positivos, solo uso de números reales o alfanuméricos.
    - `private:` La variable o método sólo es accesible dentro de la clase donde se define.
    - `public:` La variable o método es accesible en cualquier clase.

<a href="https://ibb.co/1dhQs6y"><img src="https://i.ibb.co/KLRhNw4/12.png" alt="12" border="0"></a>


- **Verificaciones y validaciones generales del programa:**
  Estas aseguran que el programa cumpla con las especificaciones asignadas.

<a href="https://ibb.co/QdbFwWK"><img src="https://i.ibb.co/4dmZrbV/13.png" alt="13" border="0"></a>


- **Agregar Producto:**
    - Selecciona la opción "1" en el menú principal.
    - Solicita al usuario los datos para el nuevo producto.
    - El código debe ser único.
    - Si se ingresan datos válidos, el producto se agrega al archivo y se muestra un mensaje de éxito.
    - **Estructura de la función:** evalúa cada dato ingresado por el usuario y se asegura que cumpla con las asignaciones de no ser así le indica al usuario a través de un mensaje.

<a href="https://ibb.co/64J1DX8"><img src="https://i.ibb.co/zSH7P6F/14.png" alt="14" border="0"></a>


- **Buscar Producto:**
    - Selecciona la opción "2" en el menú principal.
    - Solicita el código o nombre del producto que deseas buscar.
    - Se mostrarán los detalles del producto si se encuentra.
    - Si el producto no se encuentra, se mostrará un mensaje indicándolo.
    - **Estructura de la función:** Verifica que el producto deseado se encuentre dentro del archivo.

<a href="https://ibb.co/JyFyXbK"><img src="https://i.ibb.co/BrKr87t/15.png" alt="15" border="0"></a>


- **Modificar Producto:**
    - Selecciona la opción "3" en el menú principal.
    - Solicita el código del producto que deseas modificar, siendo “Código” lo único que no podrá modificar.
    - Se mostrarán los datos almacenados del producto.
    - Solicita los nuevos datos para cada atributo.
    - Los cambios se guardan en el archivo y se muestra un mensaje de éxito.
    - **Estructura de la función:** Reestructura toda la información almacenada de un producto.

<a href="https://ibb.co/RSpXL6g"><img src="https://i.ibb.co/3syxtFT/16.png" alt="16" border="0"></a>


- **Estructura de todo el menú:**
    - Permite visualizar el menú al usuario al ser ejecutado el programa.
    - Da cierre al programa.


<a href="https://ibb.co/Vt3CZV4"><img src="https://i.ibb.co/yXVk10j/17.png" alt="17" border="0"></a>

- **Salir del Programa:**
    - Selecciona la opción "4" en el menú principal.
    - El programa se cerrará de forma segura.

<a href="https://ibb.co/FVrCckx"><img src="https://i.ibb.co/4dq3Cwm/18.png" alt="18" border="0"></a>