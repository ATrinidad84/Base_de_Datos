## Práctica 8.
### Disparadores (Triggers)

Objetivo: Demostrar las operaciones que se realizan en una base de datos.

Ejercicio: Crea una base de datos llamada test que contenga una tabla llamada
alumnos con las siguientes columnas. (valor 18)

Evaluación:

Creación de la base de datos : 9 puntos.

Creación de los Disparadores(Triggers): 9 puntos.

Tabla alumnos:

● id (entero sin signo)

● nombre (cadena de caracteres)

● apellido1 (cadena de caracteres)

● apellido2 (cadena de caracteres)

● nota (número real)

Una vez creada la tabla escriba dos triggers con las siguientes características:

● Trigger 1: trigger_check_nota_before_insert

  o Se ejecuta sobre la tabla alumnos.
  
  o Se ejecuta antes de una operación de inserción.
  
  o Se almacena la leyenda 'se ingreso un registro'

● Trigger2 : trigger_check_nota_before_update
  o Se ejecuta sobre la tabla alumnos.
  
  o Se ejecuta antes de una operación de actualización.
  
  o Se ingresa la leyenda 'se modifico un regisstro'
  
Una vez creados los triggers escribe varias sentencias de inserción y actualización
sobre la tabla alumnos y verifica que los triggers se están ejecutando
correctamente.

SOLUCION

	CREATE DATABASE test;
	USE test;
	CREATE TABLE alumnos(
	id_alumno INT UNSIGNED PRIMARY KEY,
  	nombre VARCHAR(50),
  	apellido1 VARCHAR (50),
  	apellido2 VARCHAR (50),
  	nota FLOAT
	);
	CREATE TABLE registro(
	Id_registro INT AUTO_INCREMENT PRIMARY KEY,
  	Accion VARCHAR (200),
  	Fecha TIMESTAMP DEFAULT CURRENT_TIMESTAMP
	);

	DELIMITER //
	CREATE TRIGGER trigger_check_nota_before_insert BEFORE INSERT ON alumnos
	FOR EACH ROW BEGIN
	INSERT INTO registro(Accion) VALUES ('SE INGRESO UN REGISTRO');
	END//
	DELIMITER ;

	DELIMITER //
	CREATE TRIGGER trigger_check_nota_before_update BEFORE UPDATE ON alumnos
	FOR EACH ROW BEGIN
	INSERT INTO registro(Accion) VALUES ('SE MODIFICO UN REGISTRO');
	END//
	DELIMITER ;


https://www.db-fiddle.com/f/6eKd6NYRZrTrsjWonsYAkT/4

