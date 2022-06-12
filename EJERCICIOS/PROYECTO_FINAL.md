# Proyecto Final de base de datos.
### Indicaciones de lo que se debe realizar

● Diseña el modelo entidad-relación del siguiente problema.

● Crea el script para la base de datos.
Proveedores

Tenemos que diseñar una base de datos sobre proveedores y disponemos de
la siguiente información:

● De cada proveedor conocemos su nombre, dirección, ciudad, provincia y
un código de proveedor que será único para cada uno de ellos.

● Nos interesa llevar un control de las piezas que nos suministra cada
proveedor. Es importante conocer la cantidad de las diferentes piezas
que nos suministra y en qué fecha lo hace. Tenga en cuenta que un
mismo proveedor nos puede suministrar una pieza con el mismo código
en diferentes fechas. El diseño de la base de datos debe permitir
almacenar un histórico con todas las fechas y las cantidades que nos ha
proporcionado un proveedor.

● Una misma pieza puede ser suministrada por diferentes proveedores.

● De cada pieza conocemos un código que será único, nombre, color,
precio y categoría.

● Pueden existir varias categorías y para cada categoría hay un nombre y
un código de categoría único.

● Una pieza sólo puede pertenecer a una categoría.


SOLUCION


![Relacional_pzasProveedores drawio](https://user-images.githubusercontent.com/102439544/173253717-84183046-6c1e-4ed2-ab0a-a9284e119412.png)

  CREATE DATABASE proveedores;
  USE proveedores;

  --CREAMOS LA TABLA piezas
  CREATE TABLE piezas(
    codigo_pieza INT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
    nombre_pieza CHAR(100) NOT NULL,
    color CHAR(100) NOT NULL,
    precio float NOT NULL
    );


  --CREAMOS LA TABLA proveedor
  CREATE TABLE proveedor(
    codigo_proveedor INT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
    nombre_proveedor CHAR(100) NOT NULL,
    direccion CHAR(150) NOT NULL,
    ciudad CHAR(100) NOT NULL,
    provincia CHAR(100) NOT NULL
    );


  --CREAMOS LA TABLA INTERMEDIA
  CREATE TABLE suministra(
   codigo_pieza2 INT UNSIGNED,
  FOREIGN KEY (codigo_pieza2) REFERENCES piezas(codigo_pieza),
   codigo_proveedor2 INT UNSIGNED,
   FOREIGN KEY (codigo_proveedor2) REFERENCES proveedor(codigo_proveedor)
  );
 
 
  --CREAMOS LA TABLA almacen
  CREATE TABLE almacen(
   id_almacen INT UNSIGNED PRIMARY KEY,
   fecha_almacen DATE NOT NULL,
   cantidad INT UNSIGNED, 
   codigo_pieza3 INT UNSIGNED ,
  FOREIGN KEY (codigo_pieza3) REFERENCES piezas(codigo_pieza)
  );
 
  --CREAMOS LA TABLA categoria
  CREATE TABLE categoria(
   codigo_categoria INT UNSIGNED PRIMARY KEY,
   nombre_categoria CHAR(100) NOT NULL,
   codigo_pieza4 INT UNSIGNED ,
  FOREIGN KEY (codigo_pieza4) REFERENCES piezas(codigo_pieza)
  );
 

https://www.db-fiddle.com/f/hUX7e91LXpWVNZY1g7Vd6s/0



