## Práctica 9.
### Operaciones en una base de datos.
Objetivo: Demostrar las operaciones que se realizan en una base de datos, aplicar el modelo relacional y el lenguaje SQL

Evaluación: Para poder tener correcto cada ejercicio deberán de mostrar el resultado que se da en cada respuesta.

Lista el nombre de todos los productos que hay en la tabla producto.


1. Lista los nombres y los precios de todos los productos de la tabla producto.

  SELECT producto, precio_en_dolares
  FROM productos;

![Lista_articulos](https://user-images.githubusercontent.com/102439544/173251772-6bfe979f-6dc6-43ea-beb5-daa9d23ed8e4.png)


2. Lista todas las columnas de la tabla producto.

  SELECT*
  FROM productos;


![select_producto_precio](https://user-images.githubusercontent.com/102439544/173252095-3709b18f-f62b-4486-a622-122eb1f36d77.png)


3. Devuelve una lista con el nombre del producto, precio y nombre de fabricante de
todos los productos de la base de datos.


  SELECT producto, precio_en_dolares, fabricante
  FROM productos,fabricantes
  WHERE productos.codigo_producto = fabricantes.codigo_producto2;
  
  ![select_productoPrecio_fabricante](https://user-images.githubusercontent.com/102439544/173252133-a2e795f8-09e1-4430-b407-7dddc4a3f099.png)


Subconsultas (En la cláusula WHERE)

1. Devuelve todos los productos del fabricante Lenovo. (Sin utilizar INNER
JOIN).


  SELECT producto, fabricante="lENOVO"
  FROM productos, fabricantes
  WHERE productos.codigo_producto=fabricantes.codigo_producto2 ;
  
  ![subconsulta_where1](https://user-images.githubusercontent.com/102439544/173252167-d123c680-cd03-48d4-b0e1-7419cb880e92.png)


2. Devuelve todos los datos de los productos que tienen el mismo precio que el
producto más caro del fabricante Lenovo. (Sin utilizar INNER JOIN).

  SELECT precio_en_dolares=559, fabricante
  FROM productos, fabricantes
  WHERE productos.codigo_producto = fabricantes.codigo_producto2
  ;

![subconsulta_where2](https://user-images.githubusercontent.com/102439544/173252188-17401a30-95e2-4ef1-a547-454170eabe2f.png)


3. Lista el nombre del producto más caro del fabricante Lenovo.

  SELECT MAX(precio_en_dolares), fabricante="LENOVO" FROM productos, fabricantes 
  WHERE productos.codigo_producto = fabricantes.codigo_producto2 
  GROUP BY fabricantes.fabricante;
  
  ![consulta_precioMaximo](https://user-images.githubusercontent.com/102439544/173252263-54f6b312-42ea-449c-b946-523f358c661f.png)

