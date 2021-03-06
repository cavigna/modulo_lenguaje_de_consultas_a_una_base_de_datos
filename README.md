# MODULO 2 - Lenguaje de Consulta de Base de Datos | Ignacio Cavallo

## Introducción

En este módulo aprenderemos acerca de lenguajes de consulta de base de datos. Aquí iré detallando algunos de los logros y desafíos que alcancé durante el desarrollo de esta sección del curso.

## DDL | Data Definition Language

### Creación de una nueva **BASE DE DATOS**

```sql
create database primeraDB character set  utf8;
```  

### Uso de la DB

```sql  
use primeraDB;
```   

### Creación de una **TABLA**

```sql  
create table primeraTabla(
        id_prime int auto_increment,
        nombre varchar(20),
        estatura float,
        fechaNacimiento date,
        descripcion text,
        primary key(id_prime)
);
```

### Modificar el *tipo de dato* de una columna

```sql  
    alter table primeraTabla add column edad int;
```  

### **Borrar una columna**:

```sql  
    ALTER TABLE tablaMartir
    DROP COLUMN columnaABorrar;
```  

### **Borrar una tabla**:

```sql
 DROP TABLE tablaMartir;
 ```

### TRUNCATE
Borra todo el contenido de la tabla, pero no la tabla en sí:

```SQL
TRUNCATE TABLE tablaMartir;
```

## DML | Data Manipulation Language

Sintaxis de una Sentencia:

```sql
COMANDO  + CLAUSULA + OPERADOR + FUNCIÓN
SELECT   + FROM / WHERE + >= + AVG(*)
 
```

### INSERT

 ```sql
 INSERT INTO tabla_Modificar(columna1, columna2,...)
 VALUES (valor_columna1, valor_columna2, ...);
 ```

### SELECT

```sql
    SELECT columna from tabla

    SELECT columna1, columna2 from tabla

    SELECT * FROM tabla;
```

### WHERE

```sql
    SELECT * FROM nombre, apellido  from tabla  WHERE condición;
```

Condiciones *OR, AND,  > <*

```sql
SELECT * FROM tabla WHERE columna1 = valor AND columna2= valor;
SELECT * FROM tabla WHERE columna1 = valor OR  columna2= valor;
```

Borrar entrada en base a una condición

```sql
DELETE FROM tabla WHERE condición;

DELETE FROM tabla WHERE precio>1500;
```

*IN | NOT IN*

```sql
SELECT * FROM tabla WHERE campo IN(listado de valores);

SELECT * FROM empleado WHERE cargo IN ('Vendedor', 'Operario');

SELECT * FROM tabla WHERE campo  NOT IN(valor1, valor2,....);

SELECT * FROM empleado WHERE cargo NOT IN ('Vendedor', 'Operario');

```

*DISTINTO* < >

```SQL

SELECT * FROM tabla WHERE campo <> valor;


SELECT * FROM empleado WHERE cargo <> 'Jefe';
```


*BETWEEN*

```SQL

SELECT * FROM tabla WHERE campo BETWEEN valor_1 AND valor_2;


SELECT * FROM empleado WHERE fechaIngreso BETWEEN '2012-01-12' AND '2015-05-25';
SELECT * FROM empleado WHERE sueldo BETWEEN 1200 AND 2500;

```

*LIKE*
```SQL
SELECT * FROM tabla WHERE campo LIKE 'patrón'.

 --Termina con n ==> Tyron, Gordon, Marvin, Jordan, Gordon
SELECT * FROM empleado WHERE nombre like '%n'; 

-- Empieza con J ==> Jesse, Jordan, Jonah
SELECT * FROM empleado WHERE nombre like 'j%'; 

-- Empieza con A y termina Con N ==> 'A'lderso'n', 'A'nderso'n'
SELECT * FROM empleado WHERE apellidoP like 'a%n'; 

-- Contiene ar ==> H'ar'ry, 'Ar'thur, M'ar'vin
SELECT * FROM empleado WHERE nombre like '%ar%';

-- Contiene r en la segunda posición ==> F'r'eeman, P'r'ime, D'r'apper 
SELECT *  FROM empleado WHERE apellidoP like '_r%';

-- Empieza con d y contiene más de 3 caracteres.
-- Resultado ==> De Rivia,  Dent,  Draper.
-- Excluyó ==> R2 D2(Es menor a tres caracteres.)

SELECT *  FROM empleado WHERE apellidoP like 'd___%';
```

### ORDER BY

```SQL
SELECT columna_uno, columna_dos FROM tabla ORDER BY columna_dos ASC|DESC;
```

### GROUP BY

```SQL
SELECT columna_uno, ... FROM tabla GROUP BY columna_n;
```

### VIEWS

```sql
CREATE VIEW vista AS
SELECT columna1, columna2, ...
FROM tabla
WHERE condición;

CREATE VIEW datosPersonales AS 
SELECT nombre, apellidoP, edad 
FROM empleado
WHERE sueldo>1500;
```

### SUB QUERY

```SQL
SELECT * FROM tabla
WHERE condición
(SELECT selección
FROM tabla)
```

### INNER JOIN

``` SQL
SELECT columna(s)
FROM tabla1
INNER JOIN tabla2
ON tabla1.columna = tabla2.columna;
```
