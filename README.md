# Trabajo Final de Bioinformática - 1° Cuatrimestre 2020

_Se desarrolló un Software que permite  la visualización de estudios filogenéticos y filodinámicos de secuencias, con su posterior geolocalización._
_También puede verse la entrega de los trabajos parciales que se fueron dando en clase a través del siguiente [link](https://github.com/nahuelmpereyra/bioinformatica-entregas)._

***

## Autores ✒️

* **Lucio Francioni** - [franciolucio](https://github.com/franciolucio)
* **Nahuel Pereyra** - [nahuelmpereyra](https://github.com/nahuelmpereyra)
* **Leonardo Di Carlo** - [leonardodicarlo](https://github.com/leonardodicarlo)

***

## Construido con 🛠️

_El trabajo está basado sobre lenguaje Python, pero se utilizaron distintas bibliotecas y programas dedicados a la biología:_

* [Python 3](https://www.python.org/doc/) - El lenguaje utilizado para resolver la lógica de nuestro Software.
* [Django](https://docs.djangoproject.com/en/3.0/) - El framework web escrito en Python con el que armamos los componentes del Software.
* [Biopython](https://biopython.org/wiki/Documentation) - Biblioteca de Python para manejar archivos de secuencias biológicas.
* [ClustalW](http://www.clustal.org/clustal2/) - Programa instalado en local para realizar el alineamiento de secuencias biológicas.
* [IQ-Tree](http://www.iqtree.org/doc/) - Biblioteca de Python para generar estructuras de árboles filogenéticos.

***

### Instalación (Linux) 🔧

_Para correr el software localmente debemos tener instalado tanto Python 3, como las respectivas librerías que listamos anteriormente._

_Primero, nos asegurarnos que tenemos Python 3 correctamente instalado (chequeo a través del Terminal):_

```
$ python3 -V
```
_En caso de no tener la versión 3 de Python, correr los siguientes comandos:_

```
$ sudo apt-get update
$ sudo apt-get -y upgrade
```
_Además, es recomendado tener instalado *pip* para manejar los paquetes:_

```
$ sudo apt-get install -y python3-pip
```
_Segundo, instalar la biblioteca de Biopython, a través de la cual manejaremos los archivos de secuencias .FASTA:_

```
$ sudo apt-get install python-biopython
```
	
_Tercero, se debe instalar ClustalW ya que el Software lo utiliza para alinear secuencias:_

```
$ sudo apt-get update
$ sudo apt-get install clustalw
```

_Por último, debemos instalar IQ-Tree para que nuestro programa genere los diagramas de árbol filogenéticos:_

```
$ sudo apt-get update
$ sudo apt-get install iqtree
```
---

### Instalación (Windows) 🔧

_Para correr el software localmente debemos tener instalado previamente tanto Python 3, como las respectivas librerías que listamos anteriormente._

_Primero, nos asegurarnos que tenemos Python 3 correctamente instalado. Puede descargarse desde el siguiente [link](https://www.python.org/downloads/windows/):_


_Segundo, instalar la biblioteca de Biopython, a través de la cual manejaremos los archivos de secuencias .FASTA:_

_Para esto, puede instalarse por la web mediante el siguiente [link](https://biopython.org/wiki/Download), o bien mediante *PIP* desde cmd/powershell:_
	
```
pip install biopython
```
	
_Tercero, instalar ClustalW mediante el siguiente [link](http://www.clustal.org/download/current/). Con esto podremos realizar los alineamientos de secuencias._


_Por último, debemos instalar IQ-Tree desde el siguiente [link](http://www.iqtree.org/#download). Con esto dibujaremos los árboles filogenéticos._

***

##Ejecución - Paso a Paso 📋

*Para correr nuestro software localmente debemos abrir el proyecto en un IDE (cualquiera que soporte Python), y correr lo siguiente en consola:
	
```
$ python manage.py makemigrations
$ python manage.py migrate	
$ python manage.py runserver
```
*Con esto, ya debiera correr localmente nuestro programa en una nueva ventana de nuestro navegador (por defecto es el puerto localhost:8000).

*Seguidamente, podemos cargar un archivo .FASTA o .fst que sólo contenga secuencias de Ácidos Nucléicos (ADN y ARN, secuencias con A-T-G-C-U).

*El programa validara este archivo con las siguientes pautas:

* Que el archivo sea formato .FASTA o .fst.
* Que su contenido coincida con el formato de un FASTA: cabecera (>|gi|12345|gb|accessionCode) - secuencia (ATGCU).
* Que el archivo posea además en cada cabecera una locación, unificada por pips (|) con el siguiente formato ejemplo: |loc| Universidad Nacional de Quilmes, Bernal.
* Que cada cabecera presente en el archivo tenga su correspondiente secuencia asociada (no pueden quedar cabeceras sin secuencias).
* Que lo imputado en cada secuencia sean efectivamente secuencias de ADN/ARN.

*Una vez pasada efectivamente esta validación, se cargará el archivo y el programa nos redireccionará automáticamente a un nuevo link donde tendremos cargado:

*Una tabla de tipo acordeón que contiene: Secuencia - Accession de GenBank - Locación.
*Un mapa con la locación de cada una de las respectivas secuencias cargadas junto con su accession code.
*Un diagrama de árbol filogenético donde muestra las coincidencias y discrepancias entre las secuencias según las relaciones evolutivas.

*Por último, se puede descargar la información obtenida y volver a correr el programa con un nuevo archivo de secuencias.


***
