---
layout: default
---

## Introducción

SystemC es una herramienta OpenSource que proporciona un conjunto de clases y macros de C++ que permite modelar el comportamiento de sistemas. La última versión lanzada fue la v2.3.3, en noviembre de 2018.

* * *

## Requerimientos

### A. Requisitos de Hardware:

Los requerimientos de hardware están basados en los establecidos para el IDE Visual Studio Code, que es la herramienta principal para el desarrollo de las simulaciones.

- 1.6+ GHz
- 1+ GB de RAM
- 50+ GB de Almacenamiento

### B. Requisitos de Software:

Los requisitos específicos de software dependen en gran medida del sistema operativo utilizado, en este caso nos centraremos en Windows y Linux.

- **Sistema Operativo:** Windows (Windows 8.0+) o Linux (Debian 9+, Ubuntu 16.04+).
- **Compilador para C++:** gcc 10+ (Linux), o Cygwin 3.0+ (Windows).
- **GMake 4.0+**

### C. Requisitos extras para Linux:

- GLIBCXX version 3.4.21+
- GLIBC version 2.17+

* * *

## Configuración e Instalación

SystemC puede ser descargado desde la página <a href="https://www.accellera.org/downloads/standards/systemc" target="_blank">Accellera.org</a>. El cual incluye una documentación y una serie de anotaciones para la configuración e instalación en los diferentes sistemas operativos (Linux, Windows, Mac OS X, entre otros).

De acuerdo con la documentación oficial de SystemC, la instalación se basa en GMake para unificar las configuraciones en diferentes plataformas Unix y Windows. Lo que genera los archivos necesarios para compilar/instalar usando diferentes compiladores (p. ej., GNU Make o Ninja) e IDE (p. ej., Eclipse o VSCode).

Dentro de la misma documentación, nos presenta varias opciones de compiladores en los diferentes sistemas operativos y sus arquitecturas compatibles. Para ejemplificar este proceso, se lo realizará en GNU/Linux x86_64, utilizando GCC (GNU Compiler Collection). Para ello, ya se debe contar con la instalación de los paquetes <a href="https://gcc.gnu.org/" target="_blank">GCC</a> y <a href="https://www.gnu.org/software/make/" target="_blank">GMake</a> .

Tomando en consideración las anotaciones de la documentación oficial, el proceso de configuración e intalación consiste en lo siguiente:

1. **Instalación de paquetes**
```bash
# Debian
sudo apt install gcc make
# Arch Linux
sudo pacman -S gcc make
```
1. **Redirigirse al directorio con los archivos de instalación**
```bash
cd /path/to/systemc-2.3.3
```
1. **Crear un directorio temporal**
```bash 
mkdir objdir
```
1. **Adentrarse al directorio temporal**
```bash 
cd objdir
```
1. **Elegir un compilador y establecerlo como una variable de entorno**
```bash 
export CXX=g++
```
1. **Configuración para la instalación**
```bash 
../configure --prefix=/opt/systemc-2.3.3
```
    Nota: el directorio debe estar creado previamente.

1. **Compilación del paquete**
```bash
make
```
1. **Instalación del paquete**
```bash
make install
```
1. **Una vez finalizado se puede eliminar el directorio temporal**
```bash
cd ..
rm -rf objdir
```
1. **Declarar las respectivas variables de entorno**
```bash
export SYSTEMC_HOME="/opt/systemc-2.3.3"
export LD_LIBRARY_PATH="$SYSTEMC_HOME/lib-linux64"
```
    El directorio a donde apunta `SYSTEMC_HOME` debe ser el que se configuró con el parámetro `--prefix` en el paso 6.

    Opcional: Estas variables pueden ser agregadas dentro del archivo `.profile` o `.bashrc` para automatizar la exportación. Caso contrario, se deben exportar las varibles antes de compilar.

***

## Resultados

El conjunto de soluciones que proporciona SystemC, hace el proceso de abstracción de sistemas y el modelado de hardware y software sea relativamente sencillo, si se tiene clara la lógica detrás del sistema.

En el <a href="{{'/pages/example.html' | relative_url}}">ejemplo presentado</a> se logró abstraer el comportamiento básico de un entorno real (una peluquería), a un programa de SystemC haciendo uso de elementos como: `sc_module`, `sc_events`, `sc_fifo`, `sc_time`, entre otros.

***

## Conclusiones

SystemC provee un gran conjunto de recursos que permiten modelar el comportamiento de sistemas, y por lo tanto, facilita la simulación de eventos discretos. Entre las características de esta herramienta, se encuentran su propia definición de variables de tiempo, tipos de datos, clases y macros que simplifican la comunicación entre los componentes del modelo.

***

## Recomendaciones

Ya que SystemC describe todos los elementos que ofrece usando la sintaxis de C++, es recomendable primero aprender los conceptos básicos de dicho lenguaje, antes de comenzar a desarrollar modelos.
    
Por otro lado, teniendo en cuenta que también es posible modelar el comportamiento de hardware, es recomendable tener cierto conocimiento acerca de los fundamentos de compuertas lógicas, componentes electrónicos y señales digitales.