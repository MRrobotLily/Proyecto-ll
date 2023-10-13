
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

# Codigo Fuente C++

```
#include <iostream>
	#include <fstream>
	#include <vector>
	#include <string>
	#include <algorithm>
	#include <limits>
	
	using namespace std;
	
	class Producto {
	private:
	    string nombre;
	    string codigo;
	    double precio;
	    string proveedor;
	    int existencia;
	    char estado;
	    double descuento;
	
	public:
	    bool contienePalabra(const string& linea, const string& palabra);
	    bool estadoValido(char estado);
	    void cargarCodigos(vector<string>& codigos);
	    void agregar(ofstream& file, vector<string>& codigos);
	    void buscar(ifstream& file, const string& buscar);
	    void modificar(const string& codigoModificar);
	};
	
	bool Producto::estadoValido(char estado) {
	    return (estado == 'A' || estado == 'a' || estado == 'R' || estado == 'r');
	}
	
	bool Producto::contienePalabra(const string& linea, const string& palabra) {
	    string lineaMinuscula = linea;
	    transform(lineaMinuscula.begin(), lineaMinuscula.end(), lineaMinuscula.begin(), ::tolower);
	    string palabraMinuscula = palabra;
	    transform(palabraMinuscula.begin(), palabraMinuscula.end(), palabraMinuscula.begin(), ::tolower);
	
	    return lineaMinuscula.find(palabraMinuscula) != string::npos;
	}
	
	void Producto::cargarCodigos(vector<string>& codigos) {
	    ifstream file("productos.txt");
	    if (file.is_open()) {
	        string linea;
	        while (getline(file, linea)) {
	            if (linea.find("Código: ") == 0) {
	                string codigo = linea.substr(8);
	                codigos.push_back(codigo);
	            }
	        }
	        file.close();
	    }
	}
	
	void Producto::agregar(ofstream& file, vector<string>& codigos) {
	    for (int intentos = 0; intentos < 3; ++intentos) {
	        cout << "Ingrese el codigo del producto: ";
	        getline(cin, codigo);
	
	        if (!codigo.empty() &&
	            find(codigos.begin(), codigos.end(), codigo) == codigos.end()) {
	            break;
	        } else {
	            cout << "El codigo ingresado ya existe o no es valido. Ingrese un codigo único para el producto." << endl;
	        }
	
	        if (intentos == 2) {
	            cout << "Numero maximo de intentos alcanzado. Saliendo del programa." << endl;
	            return;
	        }
	    }
	
	    cout << "Ingrese el nombre del producto: ";
	    getline(cin, nombre);
	
	    cout << "Ingrese el precio del producto: ";
	    while (!(cin >> precio) || precio < 0) {
	        cout << "Valor ingresado no es válido. Ingrese un valor numerico positivo para el precio: ";
	        cin.clear();
	        cin.ignore(numeric_limits<streamsize>::max(), '\n');
	    }
	    cin.ignore(numeric_limits<streamsize>::max(), '\n');
	
	    cout << "Ingrese el proveedor del producto: ";
	    getline(cin, proveedor);
	
	    cout << "Ingrese la existencia del producto: ";
	    while (!(cin >> existencia) || existencia < 0) {
	        cout << "Valor ingresado no es valido. Ingrese un valor numerico positivo para la existencia: ";
	        cin.clear();
	        cin.ignore(numeric_limits<streamsize>::max(), '\n');
	    }
	    cin.ignore(numeric_limits<streamsize>::max(), '\n');
	
	    cout << "Ingrese el estado del producto (A = Aprobado, R = Reprobado): ";
	    while (true) {
	        cin >> estado;
	        if (estadoValido(estado)) {
	            break;
	        } else {
	            cout << "Valor ingresado no es valido. Ingrese 'A' o 'R'." << endl;
	        }
	    }
	
	    cout << "Ingrese el descuento del producto %: ";
	    while (!(cin >> descuento) || descuento < 0) {
	        cout << "Valor ingresado no es valido. Ingrese un valor numerico positivo para el descuento: ";
	        cin.clear();
	        cin.ignore(numeric_limits<streamsize>::max(), '\n');
	    }
	    cin.ignore(numeric_limits<streamsize>::max(), '\n');
	
	    codigos.push_back(codigo);
	
	    file << "Código: " << codigo << endl
	         << "Nombre: " << nombre << endl
	         << "Precio: " << precio << endl
	         << "Proveedor: " << proveedor << endl
	         << "Existencia: " << existencia << endl
	         << "Estado: " << estado << endl
	         << "Descuento: " << descuento << "%" << endl
	         << "------------------------" << endl;
	
	    cout << "\nProducto agregado con exito." << endl;
	    cout << "------------------" << endl;
	}
	
	void Producto::buscar(ifstream& file, const string& buscar) {
	    string linea;
	    bool encontrado = false;
	
	    while (getline(file, linea)) {
	        if (linea.find("Código: ") == 0 && linea.find(buscar) != string::npos) {
	            cout << "Detalles del producto:" << endl;
	            cout << linea << endl;
	
	            for (int i = 0; i < 6; i++) {
	                getline(file, linea);
	                cout << linea << endl;
	            }
	
	            encontrado = true;
	            cout << "------------------------" << endl;
	        }
	
	        if (linea.find("Nombre: ") == 0 && contienePalabra(linea, buscar)) {
	            cout << "Detalles del producto:" << endl;
	            cout << linea << endl;
	
	            for (int i = 0; i < 6; i++) {
	                getline(file, linea);
	                cout << linea << endl;
	            }
	
	            encontrado = true;
	            cout << "------------------------" << endl;
	        }
	    }
	
	    if (!encontrado) {
	        cout << "Producto no encontrado." << endl;
	    }
	}
	
	void Producto::modificar(const string& codigoModificar) {
	    ifstream original("productos.txt");
	    ofstream temp("temp.txt");
	
	    if (original.is_open() && temp.is_open()) {
	        string linea;
	        bool encontrado = false;
	
	        while (getline(original, linea)) {
	            if (linea.find("Código: " + codigoModificar) != string::npos) {
	                cout << "Modificando producto con codigo: " << codigoModificar << endl;
	                encontrado = true;
	
	                cout << "Datos actuales del producto:" << endl;
	                cout << linea << endl;
	
	                for (int i = 0; i < 6; i++) {
	                    getline(original, linea);
	                    cout << linea << endl;
	                }
	
	                Producto nuevoProducto;
	                nuevoProducto.codigo = codigoModificar;
	                cout << "Ingrese el nuevo nombre del producto: ";
	                getline(cin, nuevoProducto.nombre);
	                cout << "Ingrese el nuevo precio del producto: ";
	                while (!(cin >> nuevoProducto.precio) || nuevoProducto.precio < 0) {
	                    cout << "Valor ingresado no es valido. Ingrese un valor numerico positivo para el precio: ";
	                    cin.clear();
	                    cin.ignore(numeric_limits<streamsize>::max(), '\n');
	                }
	                cin.ignore(numeric_limits<streamsize>::max(), '\n');
	                cout << "Ingrese el nuevo proveedor del producto: ";
	                getline(cin, nuevoProducto.proveedor);
	                cout << "Ingrese la nueva existencia del producto: ";
	                while (!(cin >> nuevoProducto.existencia) || nuevoProducto.existencia < 0) {
	                    cout << "Valor ingresado no es valido. Ingrese un valor numerico positivo para la existencia: ";
	                    cin.clear();
	                    cin.ignore(numeric_limits<streamsize>::max(), '\n');
	                }
	                cin.ignore(numeric_limits<streamsize>::max(), '\n');
	                cout << "Ingrese el nuevo estado del producto (A = Aprobado, R = Reprobado): ";
	                while (true) {
	                    cin >> nuevoProducto.estado;
	                    if (nuevoProducto.estadoValido(nuevoProducto.estado)) {
	                        break;
	                    } else {
	                        cout << "Valor ingresado no es valido. Ingrese 'A' o 'R'." << endl;
	                    }
	                }
	                cout << "Ingrese el nuevo descuento del producto %: ";
	                while (!(cin >> nuevoProducto.descuento) || nuevoProducto.descuento < 0) {
	                    cout << "Valor ingresado no es valido. Ingrese un valor numerico positivo para el descuento: ";
	                    cin.clear();
	                    cin.ignore(numeric_limits<streamsize>::max(), '\n');
	                }
	                cin.ignore(numeric_limits<streamsize>::max(), '\n');
	
	                temp << "Código: " << nuevoProducto.codigo << endl
	                     << "Nombre: " << nuevoProducto.nombre << endl
	                     << "Precio: " << nuevoProducto.precio << endl
	                     << "Proveedor: " << nuevoProducto.proveedor << endl
	                     << "Existencia: " << nuevoProducto.existencia << endl
	                     << "Estado: " << nuevoProducto.estado << endl
	                     << "Descuento: " << nuevoProducto.descuento << "%" << endl
	                     << "------------------------" << endl;
	            } else {
	                temp << linea << endl;
	            }
	        }
	
	        if (!encontrado) {
	            cout << "Producto no encontrado." << endl;
	        } else {
	            cout << "Producto modificado con exito." << endl;
	        }
	
	        original.close();
	        temp.close();
	
	        remove("productos.txt");
	        rename("temp.txt", "productos.txt");
	    } else {
	        cout << "Error al abrir archivos para modificar el producto." << endl;
	    }
	}
	
	void mostrarMenu() {
	    vector<string> codigos;
	    Producto producto;
	    producto.cargarCodigos(codigos);
	
	    while (true) {
	        cout << "\nMenu Principal:" << endl;
	        cout << "------------------" << endl;
	        cout << "1. Agregar producto" << endl;
	        cout << "2. Buscar producto" << endl;
	        cout << "3. Modificar datos de un producto" << endl;
	        cout << "4. Salir" << endl;
	
	        char opcion;
	        cout << "\nSeleccione una opcion: ";
	        cin >> opcion;
	
	        cin.ignore(numeric_limits<streamsize>::max(), '\n');
	
	        if (cin.fail()) {
	            cin.clear();
	            cout << "Opcion no valida. Intente de nuevo." << endl;
	            continue;
	        }
	
	        cout << "--------------------" << endl;
	
	        if (opcion == '1') {
	            ofstream fileOut("productos.txt", ios::app);
	            if (fileOut.is_open()) {
	                producto.agregar(fileOut, codigos);
	                fileOut.close();
	            } else {
	                cout << "Error al abrir el archivo para agregar el producto." << endl;
	            }
	        } else if (opcion == '2') {
	            ifstream fileIn("productos.txt");
	            if (fileIn.is_open()) {
	                string buscar;
	                cout << "Ingrese el codigo o nombre del producto a buscar: ";
	                getline(cin, buscar);
	                cout << "----------------------" << endl;
	                producto.buscar(fileIn, buscar);
	                fileIn.close();
	            } else {
	                cout << "Error al abrir el archivo para buscar el producto." << endl;
	            }
	        } else if (opcion == '3') {
	            string codigoModificar;
	            cout << "Ingrese el codigo del producto que desea modificar: ";
	            getline(cin, codigoModificar);
	            producto.modificar(codigoModificar);
	        } else if (opcion == '4') {
	            return;
	        } else {
	            cout << "Opcion no valida. Intente de nuevo." << endl;
	        }
	    }
	}
	
	int main() {
	    mostrarMenu();
	    return 0;
	}
```
## Video del codigo en C++


# Proyecto II

## Manejo de archivos en Python
- **Descripción del Programa:**

El Sistema de Gestión de Productos es una aplicación desarrollada en Python que facilita la administración de información sobre productos. Este sistema permite realizar operaciones como agregar nuevos productos, buscar productos existentes y modificar datos de productos ya registrados. Toda la información se almacena en un archivo de texto llamado "productos.txt".

- **Requisitos previos:**
1.	Iniciar el Programa python
2.	Guarda el código en un archivo con extensión ".py".
3.	Abre una terminal y navega al directorio donde guardaste el archivo.
4.	Ejecuta el programa con el comando python nombre_del_archivo.py.

- **Menú Principal:**
Al iniciar el programa, se presenta un menú con las siguientes opciones:
1.	Agregar producto: Permite añadir un nuevo producto al sistema.
2.	Buscar producto: Busca un producto por código o nombre en el sistema.
3.	Modificar datos de un producto: Modifica la información de un producto existente.
4.	Salir: Cierra el programa.

[![image.png](https://i.postimg.cc/wM11KXCc/image.png)](https://postimg.cc/zH1zKgXV)

- **1.	Agregar Producto:**
Este proceso te guiará para agregar un nuevo producto al sistema.
Detalles del Proceso:
•	Código del Producto: Ingresa un código único y alfanumérico para el producto.
•	Datos del Producto: Proporciona el nombre, precio, proveedor, existencia, estado (Aprobado o Reprobado) y descuento del producto.
•	Guardado en Archivo: La información se guarda en el archivo "productos.t

[![image.png](https://i.postimg.cc/cHbJcKvK/image.png)](https://postimg.cc/sQ5yjg9y)

- **2.	Buscar Producto:**
Permite buscar un producto por código o nombre en el sistema.
Detalles del Proceso:
•	Ingreso de Búsqueda: Ingresa el código o nombre del producto que deseas buscar.
•	Visualización de Resultados: Se mostrarán los detalles del producto si se encuentra, de lo contrario, se indicará que el producto no fue encontrado.

[![image.png](https://i.postimg.cc/rwk54b6B/image.png)](https://postimg.cc/QHfBGfdm)

- **3.	Modificar Datos de un Producto:**
Permite modificar la información de un producto existente en el sistema.
Detalles del Proceso:
•	Ingreso del Código: Ingresa el código del producto que deseas modificar.
•	Visualización de Datos Actuales: Se muestra la información actual del producto.
•	Modificación de Datos: Ingresa los nuevos datos solicitados (nombre, precio, proveedor, existencia, estado y descuento).
Actualización en Archivo: La información se actualiza en el archivo "productos.txt".

[![image.png](https://i.postimg.cc/63gvpbL1/image.png)](https://postimg.cc/njKzdkWv)

- **4.	Salir:**
Selecciona esta opción para salir del programa.

[![image.png](https://i.postimg.cc/8kfv0DT8/image.png)](https://postimg.cc/DmFmS9W5)

**Notas Importantes*
Si el archivo "productos.txt" no existe, el programa lo creará automáticamente al agregar el primer producto.
Los códigos de productos se cargan al inicio del programa y se actualizan después de agregar o modificar productos.

Métodos:
- **5.	__init__(self):** Este es el método constructor de la clase Producto. Se encarga de inicializar las variables de instancia del objeto, como nombre, codigo, precio, etc.

[![image.png](https://i.postimg.cc/GhJ6GW8Y/image.png)](https://postimg.cc/KRj9ys5v)

- **6.	estado_valido(estado):** Este es un método estático que valida si un estado dado es válido. En este caso, valida si el estado es 'A' (Aprobado) o 'R' (Reprobado).
  
[![image.png](https://i.postimg.cc/CdpKnW2d/image.png)](https://postimg.cc/RJGmjb4z)

-**7.	contiene_palabra(linea, palabra):** Otro método estático que verifica si una palabra dada está contenida en una línea.

[![image.png](https://i.postimg.cc/WzGF2GNB/image.png)](https://postimg.cc/hQGPs77s)
  
-**8.	cargar_codigos(self):** Carga los códigos de productos desde el archivo "productos.txt". Devuelve una lista de códigos.

[![image.png](https://i.postimg.cc/ZK0nszpk/image.png)](https://postimg.cc/kB37DZTw)

-**9.	inicializar_archivo(self):** Crea el archivo "productos.txt" si no existe.

[![image.png](https://i.postimg.cc/5tmfNsLq/image.png)](https://postimg.cc/1g4kvcWf)

-**10.	obtener_valor_numerico(self, mensaje, nombre_valor):** Solicita al usuario un valor numérico (por ejemplo, precio o existencia) y lo formatea correctamente. Se asegura de que el valor ingresado sea un número válido.

[![image.png](https://i.postimg.cc/52dJBhmS/image.png)](https://postimg.cc/HV2FHPRr)

-**11.	es_codigo_valido(self, codigo):** Verifica si un código dado es alfanumérico.

[![image.png](https://i.postimg.cc/65s6c4WZ/image.png)](https://postimg.cc/dDBKt1TQ)

-**12.	agregar(self):** Agrega un nuevo producto al archivo. Solicita información al usuario, como código, nombre, precio, proveedor, existencia, estado y descuento. Luego, escribe la información en el archivo.

[![image.png](https://i.postimg.cc/CLJt19QK/image.png)](https://postimg.cc/hfzMZZgF)
[![image.png](https://i.postimg.cc/W3PSS7HK/image.png)](https://postimg.cc/PL2m51hz)
[![image.png](https://i.postimg.cc/prWCMLxJ/image.png)](https://postimg.cc/tZcWhyss)

-**13.	buscar(self, buscar):** Busca un producto por código o nombre en el archivo y muestra los detalles si lo encuentra.

[![image.png](https://i.postimg.cc/VkrR8Typ/image.png)](https://postimg.cc/Js8J3pz5)
[![image.png](https://i.postimg.cc/NM48DvT9/image.png)](https://postimg.cc/TLKW2Stf)

-**14.	modificar(self, codigo_modificar):** Permite al usuario modificar los datos de un producto existente en el archivo. Busca el producto por código, muestra los datos actuales y solicita la nueva información al usuario. Luego, actualiza el archivo.

[![image.png](https://i.postimg.cc/4NM6B5K5/image.png)](https://postimg.cc/D8r4z1PJ)
[![image.png](https://i.postimg.cc/PxtYPVct/image.png)](https://postimg.cc/4KSm0PsM)
[![image.png](https://i.postimg.cc/4dNHJ77y/image.png)](https://postimg.cc/HJRkzLt1)
[![image.png](https://i.postimg.cc/0jhzdVtK/image.png)](https://postimg.cc/ZvFYJxzJ)

-**15.	mostrar_menu():** La función principal que maneja el menú de opciones para el usuario. Muestra las opciones, recoge la selección del usuario y ejecuta la acción correspondiente.

[![image.png](https://i.postimg.cc/FKG1nrW4/image.png)](https://postimg.cc/KKkZ12hq)
[![image.png](https://i.postimg.cc/FKG1nrW4/image.png)](https://postimg.cc/KKkZ12hq)
[![image.png](https://i.postimg.cc/6qVQnBGg/image.png)](https://postimg.cc/ctHZNyhB)

-**16.	__main__:** Punto de entrada principal del programa. Inicializa un objeto de la clase Producto y llama a mostrar_menu().

[![image.png](https://i.postimg.cc/nrxFHNwk/image.png)](https://postimg.cc/FdP5pCvd)

# Codigo Fuente Python

```
import os

class Producto:
    def __init__(self):
        # Declaración de variables de un producto
        self.nombre = ""
        self.codigo = ""
        self.precio = 0.0
        self.proveedor = ""
        self.existencia = 0
        self.estado = ""
        self.descuento = 0.0

    @staticmethod
    def estado_valido(estado):
        # Método para validar el estado del producto (Aprobado o Reprobado)
        return estado.lower() in ['a', 'r']

    @staticmethod
    def contiene_palabra(linea, palabra):
        # Método para verificar si una palabra está contenida en una línea
        return palabra.lower() in linea.lower()

    def cargar_codigos(self):
        # Cargar códigos de productos desde el archivo
        codigos = []
        ruta_archivo = os.path.join(os.path.dirname(os.path.realpath(__file__)), "productos.txt")

        if os.path.exists(ruta_archivo):
            with open(ruta_archivo, "r") as file:
                for linea in file:
                    if linea.startswith("Código: "):
                        codigo = linea[8:].strip()
                        codigos.append(codigo)
        return codigos

    def inicializar_archivo(self):
        # Crear el archivo si no existe
        directorio_actual = os.path.dirname(os.path.realpath(__file__))
        ruta_archivo = os.path.join(directorio_actual, "productos.txt")

        if not os.path.exists(ruta_archivo):
            try:
                with open(ruta_archivo, "w"):
                    pass
            except Exception as e:
                print(f"Error al inicializar el archivo: {e}")

    def obtener_valor_numerico(self, mensaje, nombre_valor):
        # Obtener un valor numérico positivo desde la entrada del usuario
        while True:
            try:
                valor = float(input(mensaje))
                if valor >= 0:
                    return valor
                else:
                    print(f"Valor ingresado no es válido. Ingrese un valor numérico positivo para {nombre_valor}.")
            except ValueError:
                print(f"Valor ingresado no es válido. Ingrese un valor numérico positivo para {nombre_valor}.")

    def es_codigo_valido(self, codigo):
        # Verificar si el código es alfanumérico
        return codigo.isalnum()

    def agregar(self):
        # Agregar un nuevo producto al archivo
        self.inicializar_archivo()
        codigos = self.cargar_codigos()

        for intentos in range(3):
            self.codigo = input("Ingrese el código del producto: ")

            if self.codigo and self.codigo not in codigos and self.es_codigo_valido(self.codigo):
                break
            else:
                print("El código ingresado ya existe o no es válido. Ingrese un código único y válido para el producto.")
                if intentos == 2:
                    print("Número máximo de intentos alcanzado. Cancelando la operación.")
                    return

        self.nombre = input("Ingrese el nombre del producto: ")
        self.precio = self.obtener_valor_numerico("Ingrese el precio del producto: ", "el precio")
        self.proveedor = input("Ingrese el proveedor del producto: ")
        self.existencia = int(self.obtener_valor_numerico("Ingrese la existencia del producto: ", "la existencia"))

        self.estado = input("Ingrese el estado del producto (A = Aprobado, R = Reprobado): ").lower()
        while not self.estado_valido(self.estado):
            print("Valor ingresado no es válido. Ingrese 'A' o 'R'.")
            self.estado = input("Ingrese el estado del producto (A = Aprobado, R = Reprobado): ").lower()

        self.descuento = self.obtener_valor_numerico("Ingrese el descuento del producto %: ", "el descuento")

        codigos.append(self.codigo)

        ruta_archivo = os.path.join(os.path.dirname(os.path.realpath(__file__)), "productos.txt")

        try:
            with open(ruta_archivo, "a") as file:
                file.write(f"Código: {self.codigo}\n")
                file.write(f"Nombre: {self.nombre}\n")
                file.write(f"Precio: {self.precio}\n")
                file.write(f"Proveedor: {self.proveedor}\n")
                file.write(f"Existencia: {self.existencia}\n")
                file.write(f"Estado: {self.estado}\n")
                file.write(f"Descuento: {self.descuento}%\n")
                file.write("------------------------\n")
        except Exception as e:
            print(f"Error al escribir en el archivo: {e}")

        print("\nProducto agregado con éxito.")
        print("------------------")

    def buscar(self, buscar):
        # Buscar un producto por código o nombre en el archivo
        ruta_archivo = os.path.join(os.path.dirname(os.path.realpath(__file__)), "productos.txt")
        with open(ruta_archivo, "r") as file:
            encontrado = False
            for linea in file:
                if linea.startswith("Código: ") and buscar in linea:
                    print("Detalles del producto:")
                    print(linea.strip())
                    for _ in range(6):
                        print(file.readline().strip())
                    encontrado = True
                    print("------------------------")
                    break  # Rompe el bucle una vez que se ha encontrado un producto por código

                if linea.startswith("Nombre: ") and self.contiene_palabra(linea, buscar):
                    print("Detalles del producto:")
                    print(linea.strip())
                    for _ in range(6):
                        print(file.readline().strip())
                    encontrado = True
                    print("------------------------")
                    break  # Rompe el bucle una vez que se ha encontrado un producto por nombre

            if not encontrado:
                print("Producto no encontrado.")

    def modificar(self, codigo_modificar):
        # Modificar los datos de un producto en el archivo
        self.inicializar_archivo()
        ruta_original = os.path.join(os.path.dirname(os.path.realpath(__file__)), "productos.txt")
        ruta_temporal = os.path.join(os.path.dirname(os.path.realpath(__file__)), "temp.txt")
        
        with open(ruta_original, "r") as original, open(ruta_temporal, "w") as temp:
            encontrado = False
            for linea in original:
                if f"Código: {codigo_modificar}" in linea:
                    print(f"Modificando producto con código: {codigo_modificar}")
                    encontrado = True

                    print("Datos actuales del producto:")
                    print(linea.strip())
                    for _ in range(6):
                        print(original.readline().strip())

                    nuevo_producto = Producto()
                    nuevo_producto.codigo = codigo_modificar
                    nuevo_producto.nombre = input("Ingrese el nuevo nombre del producto: ")
                    nuevo_producto.precio = self.obtener_valor_numerico("Ingrese el nuevo precio del producto: ", "el precio")
                    nuevo_producto.proveedor = input("Ingrese el nuevo proveedor del producto: ")
                    nuevo_producto.existencia = int(self.obtener_valor_numerico("Ingrese la nueva existencia del producto: ", "la existencia"))

                    nuevo_producto.estado = input("Ingrese el nuevo estado del producto (A = Aprobado, R = Reprobado): ").lower()
                    while not nuevo_producto.estado_valido(nuevo_producto.estado):
                        print("Valor ingresado no es válido. Ingrese 'A' o 'R'.")
                        nuevo_producto.estado = input("Ingrese el nuevo estado del producto (A = Aprobado, R = Reprobado): ").lower()

                    nuevo_producto.descuento = self.obtener_valor_numerico("Ingrese el nuevo descuento del producto %: ", "el descuento")

                    temp.write(f"Código: {nuevo_producto.codigo}\n")
                    temp.write(f"Nombre: {nuevo_producto.nombre}\n")
                    temp.write(f"Precio: {nuevo_producto.precio}\n")
                    temp.write(f"Proveedor: {nuevo_producto.proveedor}\n")
                    temp.write(f"Existencia: {nuevo_producto.existencia}\n")
                    temp.write(f"Estado: {nuevo_producto.estado}\n")
                    temp.write(f"Descuento: {nuevo_producto.descuento}%\n")
                    temp.write("------------------------\n")
                else:
                    temp.write(linea)

            if not encontrado:
                print("Producto no encontrado.")
            else:
                print("Producto modificado con éxito.")

        os.remove(ruta_original)
        os.rename(ruta_temporal, ruta_original)

def mostrar_menu():
    # Función principal que muestra el menú y gestiona las opciones
    producto = Producto()

    # Cargar los códigos existentes al inicio del programa
    codigos = producto.cargar_codigos()

    while True:
        print("\nMenu Principal:")
        print("------------------")
        print("1. Agregar producto")
        print("2. Buscar producto")
        print("3. Modificar datos de un producto")
        print("4. Salir")

        opcion = input("\nSeleccione una opción: ")

        try:
            opcion = int(opcion)
        except ValueError:
            print("Opción no válida. Intente de nuevo.")
            continue

        print("------------------")

        if opcion == 1:
            producto.agregar()
            # Actualizar la lista de códigos después de agregar un producto
            codigos = producto.cargar_codigos()
        elif opcion == 2:
            buscar = input("Ingrese el código o nombre del producto a buscar: ")
            print("----------------------")
            producto.buscar(buscar)
        elif opcion == 3:
            codigo_modificar = input("Ingrese el código del producto que desea modificar: ")
            producto.modificar(codigo_modificar)
            # Actualizar la lista de códigos después de modificar un producto
            codigos = producto.cargar_codigos()
        elif opcion == 4:
            return
        else:
            print("Opción no válida. Intente de nuevo.")

if __name__ == '__main__':
    mostrar_menu()

```
## Video del codigo en Python

[![Alt text](https://img.youtube.com/vi/k1Jaqvy-fbU/0.jpg)](https://www.youtube.com/watch?v=k1Jaqvy-fbU)

