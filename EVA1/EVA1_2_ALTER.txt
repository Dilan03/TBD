MySQL Shell 8.0.32

Copyright (c) 2016, 2023, Oracle and/or its affiliates.
Oracle is a registered trademark of Oracle Corporation and/or its affiliates.
Other names may be trademarks of their respective owners.

Type '\help' or '\?' for help; '\quit' to exit.
 MySQL  JS > sql
ReferenceError: sql is not defined
 MySQL  JS > \sql
Switching to SQL mode... Commands end with ;
 MySQL  SQL > \connect --mc root@localhost
Creating a Classic session to 'root@localhost'
Fetching global names for auto-completion... Press ^C to stop.
Your MySQL connection id is 9
Server version: 8.0.31 MySQL Community Server - GPL
No default schema selected; type \use <schema> to set one.
 MySQL  localhost:3306 ssl  SQL > show tables;
ERROR: 1046 (3D000): No database selected
 MySQL  localhost:3306 ssl  SQL > show databases;
+--------------------+
| Database           |
+--------------------+
| evaluacion_1       |
| information_schema |
| mysql              |
| performance_schema |
| sakila             |
| sys                |
| world              |
+--------------------+
7 rows in set (0.0015 sec)
 MySQL  localhost:3306 ssl  SQL > \use evalucion_1;
MySQL Error 1049: Unknown database 'evalucion_1'
 MySQL  localhost:3306 ssl  SQL > \use evaluacion_1;
Default schema set to `evaluacion_1`.
Fetching global names, object names from `evaluacion_1` for auto-completion... Press ^C to stop.
 MySQL  localhost:3306 ssl  evaluacion_1  SQL > show tables;
+------------------------+
| Tables_in_evaluacion_1 |
+------------------------+
| primer_tabla           |
+------------------------+
1 row in set (0.0015 sec)
 MySQL  localhost:3306 ssl  evaluacion_1  SQL > desc primer_tabla;
+--------+-------------+------+-----+---------+-------+
| Field  | Type        | Null | Key | Default | Extra |
+--------+-------------+------+-----+---------+-------+
| id     | int         | YES  |     | NULL    |       |
| nombre | varchar(50) | YES  |     | NULL    |       |
+--------+-------------+------+-----+---------+-------+
2 rows in set (0.0016 sec)
 MySQL  localhost:3306 ssl  evaluacion_1  SQL > alter table primer_tabla
                                             -> add column edad int
                                             -> after nombre;
Query OK, 0 rows affected (0.0357 sec)

Records: 0  Duplicates: 0  Warnings: 0
 MySQL  localhost:3306 ssl  evaluacion_1  SQL > desc primer_tabla;
+--------+-------------+------+-----+---------+-------+
| Field  | Type        | Null | Key | Default | Extra |
+--------+-------------+------+-----+---------+-------+
| id     | int         | YES  |     | NULL    |       |
| nombre | varchar(50) | YES  |     | NULL    |       |
| edad   | int         | YES  |     | NULL    |       |
+--------+-------------+------+-----+---------+-------+
3 rows in set (0.0019 sec)
 MySQL  localhost:3306 ssl  evaluacion_1  SQL > alter table primer_tabla
                                             -> drop column edad;
Query OK, 0 rows affected (0.0117 sec)

Records: 0  Duplicates: 0  Warnings: 0
 MySQL  localhost:3306 ssl  evaluacion_1  SQL > desc primer_tabla;
+--------+-------------+------+-----+---------+-------+
| Field  | Type        | Null | Key | Default | Extra |
+--------+-------------+------+-----+---------+-------+
| id     | int         | YES  |     | NULL    |       |
| nombre | varchar(50) | YES  |     | NULL    |       |
+--------+-------------+------+-----+---------+-------+
2 rows in set (0.0017 sec)
 MySQL  localhost:3306 ssl  evaluacion_1  SQL > alter table primer_tabla
                                             -> add clumn apellido varchar(50)
                                             -> after nombre;
ERROR: 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'apellido varchar(50)
after nombre' at line 2
 MySQL  localhost:3306 ssl  evaluacion_1  SQL > alter table primer_tabla add column apellido varchar(50) after nombre;
Query OK, 0 rows affected (0.0091 sec)

Records: 0  Duplicates: 0  Warnings: 0
 MySQL  localhost:3306 ssl  evaluacion_1  SQL > desc primer_tabla;
+----------+-------------+------+-----+---------+-------+
| Field    | Type        | Null | Key | Default | Extra |
+----------+-------------+------+-----+---------+-------+
| id       | int         | YES  |     | NULL    |       |
| nombre   | varchar(50) | YES  |     | NULL    |       |
| apellido | varchar(50) | YES  |     | NULL    |       |
+----------+-------------+------+-----+---------+-------+
3 rows in set (0.0016 sec)
 MySQL  localhost:3306 ssl  evaluacion_1  SQL > alter table primer_tabla
                                             -> rename column apellidos to nuevo_apellidos;
ERROR: 1054 (42S22): Unknown column 'apellidos' in 'primer_tabla'
 MySQL  localhost:3306 ssl  evaluacion_1  SQL > alter table primer_tabla rename column apellido to nuevo_apellidos;
Query OK, 0 rows affected (0.0085 sec)

Records: 0  Duplicates: 0  Warnings: 0
 MySQL  localhost:3306 ssl  evaluacion_1  SQL > desc primer_tabla;
+-----------------+-------------+------+-----+---------+-------+
| Field           | Type        | Null | Key | Default | Extra |
+-----------------+-------------+------+-----+---------+-------+
| id              | int         | YES  |     | NULL    |       |
| nombre          | varchar(50) | YES  |     | NULL    |       |
| nuevo_apellidos | varchar(50) | YES  |     | NULL    |       |
+-----------------+-------------+------+-----+---------+-------+
3 rows in set (0.0017 sec)
 MySQL  localhost:3306 ssl  evaluacion_1  SQL > alter table primer_tabla
                                             -> midify column nuevo_apellidos varchar(50) to varchar(250);
ERROR: 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'midify column nuevo_apellidos varchar(50) to varchar(250)' at line 2
 MySQL  localhost:3306 ssl  evaluacion_1  SQL > alter table primer_tabla midify column nuevo_apellidos varchar(50) to varchar(250);
ERROR: 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'midify column nuevo_apellidos varchar(50) to varchar(250)' at line 1
 MySQL  localhost:3306 ssl  evaluacion_1  SQL > alter table primer_tabla modify column nuevo_apellidos varchar(50) to varchar(250);
ERROR: 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'to varchar(250)' at line 1
 MySQL  localhost:3306 ssl  evaluacion_1  SQL > alter table primer_tabla modify column nuevo_apellidos varchar(50) to nuevo_apellidos varchar(250);
ERROR: 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'to nuevo_apellidos varchar(250)' at line 1
 MySQL  localhost:3306 ssl  evaluacion_1  SQL > alter table primer_tabla modify column nuevo_apellidos varchar(50) to nuevo_apellidos,varchar(250);
ERROR: 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'to nuevo_apellidos,varchar(250)' at line 1
 MySQL  localhost:3306 ssl  evaluacion_1  SQL > alter table primer_tabla modify column nuevo_apellidos,varchar(50) to nuevo_apellidos,varchar(250);
ERROR: 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ',varchar(50) to nuevo_apellidos,varchar(250)' at line 1
 MySQL  localhost:3306 ssl  evaluacion_1  SQL > alter table primer_tabla modify column nuevo_apellidos varchar(255), nombre varchar(255)
                                             -> ;
ERROR: 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'nombre varchar(255)' at line 1
 MySQL  localhost:3306 ssl  evaluacion_1  SQL > alter table primer_tabla modify nuevo_apellidos varchar(255), nombre varchar(255);
ERROR: 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'nombre varchar(255)' at line 1
 MySQL  localhost:3306 ssl  evaluacion_1  SQL > alter table primer_tabla
                                             -> modify nuevo_apellidos varchar(255);
Query OK, 0 rows affected (0.0366 sec)

Records: 0  Duplicates: 0  Warnings: 0
 MySQL  localhost:3306 ssl  evaluacion_1  SQL > desc primer_tabla;
+-----------------+--------------+------+-----+---------+-------+
| Field           | Type         | Null | Key | Default | Extra |
+-----------------+--------------+------+-----+---------+-------+
| id              | int          | YES  |     | NULL    |       |
| nombre          | varchar(50)  | YES  |     | NULL    |       |
| nuevo_apellidos | varchar(255) | YES  |     | NULL    |       |
+-----------------+--------------+------+-----+---------+-------+
3 rows in set (0.0016 sec)
 MySQL  localhost:3306 ssl  evaluacion_1  SQL > alter table primer_tabla modify nombre varchar(255);
Query OK, 0 rows affected (0.0297 sec)

Records: 0  Duplicates: 0  Warnings: 0
 MySQL  localhost:3306 ssl  evaluacion_1  SQL > create table empleados
                                             -> id int,
                                             -> nombre varchar(50),
                                             -> apellido varchar(50),
                                             -> fecha d;
ERROR: 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'id int,
nombre varchar(50),
apellido varchar(50),
fecha d' at line 2
 MySQL  localhost:3306 ssl  evaluacion_1  SQL > create table empleados(
                                             ->     id int,
                                             ->     nombre varchar(50),
                                             ->     apellido varchar(50),
                                             ->     fecha_naciminento datetime,
                                             ->     rfc varchar(13),
                                             ->     ciudad_nacimiento text,
                                             ->     estado int,
                                             ->     numero_tel varchar
                                             -> );
ERROR: 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ')' at line 10
 MySQL  localhost:3306 ssl  evaluacion_1  SQL > create table empleados(
                                             ->     id int,
                                             ->     nombre varchar(50),
                                             ->     apellido varchar(50),
                                             ->     fecha_naciminento datetime,
                                             ->     rfc varchar(13),
                                             ->     ciudad_nacimiento text,
                                             ->     estado int,
                                             ->     numero_tel varchar(50)
                                             -> );
Query OK, 0 rows affected (0.0196 sec)
 MySQL  localhost:3306 ssl  evaluacion_1  SQL > desc empleados;
+-------------------+-------------+------+-----+---------+-------+
| Field             | Type        | Null | Key | Default | Extra |
+-------------------+-------------+------+-----+---------+-------+
| id                | int         | YES  |     | NULL    |       |
| nombre            | varchar(50) | YES  |     | NULL    |       |
| apellido          | varchar(50) | YES  |     | NULL    |       |
| fecha_naciminento | datetime    | YES  |     | NULL    |       |
| rfc               | varchar(13) | YES  |     | NULL    |       |
| ciudad_nacimiento | text        | YES  |     | NULL    |       |
| estado            | int         | YES  |     | NULL    |       |
| numero_tel        | varchar(50) | YES  |     | NULL    |       |
+-------------------+-------------+------+-----+---------+-------+
8 rows in set (0.0022 sec)
 MySQL  localhost:3306 ssl  evaluacion_1  SQL > ALTER TABLE empleados
                                             -> ADD column nss varchar(20)
                                             -> after rfc;
Query OK, 0 rows affected (0.0147 sec)

Records: 0  Duplicates: 0  Warnings: 0
 MySQL  localhost:3306 ssl  evaluacion_1  SQL > desc empleados;
+-------------------+-------------+------+-----+---------+-------+
| Field             | Type        | Null | Key | Default | Extra |
+-------------------+-------------+------+-----+---------+-------+
| id                | int         | YES  |     | NULL    |       |
| nombre            | varchar(50) | YES  |     | NULL    |       |
| apellido          | varchar(50) | YES  |     | NULL    |       |
| fecha_naciminento | datetime    | YES  |     | NULL    |       |
| rfc               | varchar(13) | YES  |     | NULL    |       |
| nss               | varchar(20) | YES  |     | NULL    |       |
| ciudad_nacimiento | text        | YES  |     | NULL    |       |
| estado            | int         | YES  |     | NULL    |       |
| numero_tel        | varchar(50) | YES  |     | NULL    |       |
+-------------------+-------------+------+-----+---------+-------+
9 rows in set (0.0017 sec)
 MySQL  localhost:3306 ssl  evaluacion_1  SQL > ALTER TABLE empleados
                                             -> ADD column pais varchar(10)
                                             -> after estado;
Query OK, 0 rows affected (0.0109 sec)

Records: 0  Duplicates: 0  Warnings: 0
 MySQL  localhost:3306 ssl  evaluacion_1  SQL > desc empleados;
+-------------------+-------------+------+-----+---------+-------+
| Field             | Type        | Null | Key | Default | Extra |
+-------------------+-------------+------+-----+---------+-------+
| id                | int         | YES  |     | NULL    |       |
| nombre            | varchar(50) | YES  |     | NULL    |       |
| apellido          | varchar(50) | YES  |     | NULL    |       |
| fecha_naciminento | datetime    | YES  |     | NULL    |       |
| rfc               | varchar(13) | YES  |     | NULL    |       |
| nss               | varchar(20) | YES  |     | NULL    |       |
| ciudad_nacimiento | text        | YES  |     | NULL    |       |
| estado            | int         | YES  |     | NULL    |       |
| pais              | varchar(10) | YES  |     | NULL    |       |
| numero_tel        | varchar(50) | YES  |     | NULL    |       |
+-------------------+-------------+------+-----+---------+-------+
10 rows in set (0.0016 sec)
 MySQL  localhost:3306 ssl  evaluacion_1  SQL > ALTER TABLE empleados
                                             -> RENAME COLUMN numero_tel TO celular;
Query OK, 0 rows affected (0.0107 sec)

Records: 0  Duplicates: 0  Warnings: 0
 MySQL  localhost:3306 ssl  evaluacion_1  SQL > desc empleados;
+-------------------+-------------+------+-----+---------+-------+
| Field             | Type        | Null | Key | Default | Extra |
+-------------------+-------------+------+-----+---------+-------+
| id                | int         | YES  |     | NULL    |       |
| nombre            | varchar(50) | YES  |     | NULL    |       |
| apellido          | varchar(50) | YES  |     | NULL    |       |
| fecha_naciminento | datetime    | YES  |     | NULL    |       |
| rfc               | varchar(13) | YES  |     | NULL    |       |
| nss               | varchar(20) | YES  |     | NULL    |       |
| ciudad_nacimiento | text        | YES  |     | NULL    |       |
| estado            | int         | YES  |     | NULL    |       |
| pais              | varchar(10) | YES  |     | NULL    |       |
| celular           | varchar(50) | YES  |     | NULL    |       |
+-------------------+-------------+------+-----+---------+-------+
10 rows in set (0.0017 sec)
 MySQL  localhost:3306 ssl  evaluacion_1  SQL > ALTER TABLE empleados
                                             -> ADD column tel_fijo varchar(50)
                                             -> after celular;
Query OK, 0 rows affected (0.0097 sec)

Records: 0  Duplicates: 0  Warnings: 0
 MySQL  localhost:3306 ssl  evaluacion_1  SQL > desc empleados;
+-------------------+-------------+------+-----+---------+-------+
| Field             | Type        | Null | Key | Default | Extra |
+-------------------+-------------+------+-----+---------+-------+
| id                | int         | YES  |     | NULL    |       |
| nombre            | varchar(50) | YES  |     | NULL    |       |
| apellido          | varchar(50) | YES  |     | NULL    |       |
| fecha_naciminento | datetime    | YES  |     | NULL    |       |
| rfc               | varchar(13) | YES  |     | NULL    |       |
| nss               | varchar(20) | YES  |     | NULL    |       |
| ciudad_nacimiento | text        | YES  |     | NULL    |       |
| estado            | int         | YES  |     | NULL    |       |
| pais              | varchar(10) | YES  |     | NULL    |       |
| celular           | varchar(50) | YES  |     | NULL    |       |
| tel_fijo          | varchar(50) | YES  |     | NULL    |       |
+-------------------+-------------+------+-----+---------+-------+
11 rows in set (0.0017 sec)
 MySQL  localhost:3306 ssl  evaluacion_1  SQL > ALTER TABLE empleados
                                             -> ADD column id_depto int
                                             -> after id;
Query OK, 0 rows affected (0.0151 sec)

Records: 0  Duplicates: 0  Warnings: 0
 MySQL  localhost:3306 ssl  evaluacion_1  SQL > desc empleados;
+-------------------+-------------+------+-----+---------+-------+
| Field             | Type        | Null | Key | Default | Extra |
+-------------------+-------------+------+-----+---------+-------+
| id                | int         | YES  |     | NULL    |       |
| id_depto          | int         | YES  |     | NULL    |       |
| nombre            | varchar(50) | YES  |     | NULL    |       |
| apellido          | varchar(50) | YES  |     | NULL    |       |
| fecha_naciminento | datetime    | YES  |     | NULL    |       |
| rfc               | varchar(13) | YES  |     | NULL    |       |
| nss               | varchar(20) | YES  |     | NULL    |       |
| ciudad_nacimiento | text        | YES  |     | NULL    |       |
| estado            | int         | YES  |     | NULL    |       |
| pais              | varchar(10) | YES  |     | NULL    |       |
| celular           | varchar(50) | YES  |     | NULL    |       |
| tel_fijo          | varchar(50) | YES  |     | NULL    |       |
+-------------------+-------------+------+-----+---------+-------+
12 rows in set (0.0017 sec)
 MySQL  localhost:3306 ssl  evaluacion_1  SQL > ALTER TABLE empleados
                                             -> ADD COLUMN iniciales varchar(10)
                                             -> AFTER apellido;
Query OK, 0 rows affected (0.0094 sec)

Records: 0  Duplicates: 0  Warnings: 0
 MySQL  localhost:3306 ssl  evaluacion_1  SQL > desc empleados;
+-------------------+-------------+------+-----+---------+-------+
| Field             | Type        | Null | Key | Default | Extra |
+-------------------+-------------+------+-----+---------+-------+
| id                | int         | YES  |     | NULL    |       |
| id_depto          | int         | YES  |     | NULL    |       |
| nombre            | varchar(50) | YES  |     | NULL    |       |
| apellido          | varchar(50) | YES  |     | NULL    |       |
| iniciales         | varchar(10) | YES  |     | NULL    |       |
| fecha_naciminento | datetime    | YES  |     | NULL    |       |
| rfc               | varchar(13) | YES  |     | NULL    |       |
| nss               | varchar(20) | YES  |     | NULL    |       |
| ciudad_nacimiento | text        | YES  |     | NULL    |       |
| estado            | int         | YES  |     | NULL    |       |
| pais              | varchar(10) | YES  |     | NULL    |       |
| celular           | varchar(50) | YES  |     | NULL    |       |
| tel_fijo          | varchar(50) | YES  |     | NULL    |       |
+-------------------+-------------+------+-----+---------+-------+
13 rows in set (0.0017 sec)
 MySQL  localhost:3306 ssl  evaluacion_1  SQL >