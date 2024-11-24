# Laboratorio 3-2

*Los comandos SQL están al final del archivo*

## Usando la consola

### Copiamos los archivos que necesitamos desde el s3 al hadoop

<img width="1440" alt="Pasted Graphic 24" src="https://github.com/user-attachments/assets/6bb31c67-d1ad-4201-85bd-e0a74296a895">

### Ahora podemos crear las tablas directamente desde la instancia usando beeline

<img width="1440" alt="Pasted Graphic 26" src="https://github.com/user-attachments/assets/64e83106-59e6-4e5c-b172-0cbe7d98c1ba">

<img width="1440" alt="Pasted Graphic 27" src="https://github.com/user-attachments/assets/21b9d5bd-0693-4c9d-b8ff-26129c36b704">

<img width="1440" alt="Pasted Graphic 28" src="https://github.com/user-attachments/assets/cc67ce1b-2576-4c85-a275-f6989591b6ef">

<img width="1440" alt="Pasted Graphic 29" src="https://github.com/user-attachments/assets/b4658291-6b09-4955-a0fd-426f30f76b50">

## También podemos crear las tablas y hacer las consultas usando la GUI de hive en hue

<img width="1440" alt="Pasted Graphic 21" src="https://github.com/user-attachments/assets/323363ff-999b-471f-aad7-544c02ff3109">

<img width="1440" alt="Pasted Graphic 22" src="https://github.com/user-attachments/assets/8d6866cd-9645-4034-b9aa-57772b53cb5f">

<img width="1440" alt="Pasted Graphic 23" src="https://github.com/user-attachments/assets/86a104b9-3a0f-43b8-a95d-33125447f497">

<img width="1440" alt="Pasted Graphic 30" src="https://github.com/user-attachments/assets/708fc167-546b-48b9-8979-7fa35e942e4f">

<img width="1440" alt="Pasted Graphic 31" src="https://github.com/user-attachments/assets/f07993a1-a6f6-4b40-88d9-4b2860441adc">

<img width="1440" alt="Pasted Graphic 32" src="https://github.com/user-attachments/assets/898a62e3-88d3-4d4c-8c42-553563d1caac">

<img width="1440" alt="Pasted Graphic 33" src="https://github.com/user-attachments/assets/7548a598-0a3e-4dad-a891-69a8c1cd63cc">

<img width="1440" alt="Pasted Graphic 34" src="https://github.com/user-attachments/assets/0b656084-6cd3-4855-8279-44d0f8f51563">

<img width="1440" alt="Pasted Graphic 35" src="https://github.com/user-attachments/assets/ff63b71c-f50b-425b-9d30-3fbeb004bf0d">

<img width="1440" alt="Pasted Graphic 36" src="https://github.com/user-attachments/assets/9dc733af-6e67-409d-8584-e19d514caffb">

<img width="1440" alt="Pasted Graphic 37" src="https://github.com/user-attachments/assets/827070a8-7347-4348-9d8e-e8449cd40c3c">

## Comandos usados en hive 

```sql
-- Mostrar las bases de datos
SHOW DATABASES;

-- Mostrar las tablas que existen en el momento.
SHOW TABLES;

CREATE TABLE hdilabhive (id INT, country STRING, hdi FLOAT, lifeex INT, mysch INT, eysch INT, gni INT) 
ROW FORMAT DELIMITED FIELDS TERMINATED BY ','
STORED AS TEXTFILE

-- Mostrar de nuevo las tablas que existen en el momento pare verificar la creación de la tabla 'hdilabhive'.
SHOW TABLES;

-- Comando para mostrar las 10 primeras entradas de la base de datos 'hdilabhive'
SELECT * FROM hdilabhive LIMIT 10;

-- Comando para mostrar todas las entradas de la base de datos 'hdilabhive'
SELECT * FROM hdilabhive;

-- Creamos la tabla nueva de prueba llamada exportdata, verificando cuales son los datos del archivo que vamos a subir.
CREATE TABLE exportdata (id INT,country STRING, hdi FLOAT, lifeex INT, myschool INT, eyschool INT, gni INT, gni2 INT, nihdi FLOAT )
ROW FORMAT DELIMITED  FIELDS TERMINATED BY ',' 
STORED AS TEXTFILE;

-- Verificaos la creación de la tabla.
SHOW TABLES;

-- Cargar los datos en la tabla exportdata desde HDFS.
LOAD DATA INPATH '/user/hadoop/datasets/onu/hdi/hdi-data.csv' INTO TABLE exportdata;

-- Cargamos los datos desde la tabla con un límite de 10 salidas para que no me muestre todo.
SELECT * FROM exportdata;

-- Creamos tabla externa en hadoop por GUI.
CREATE EXTERNAL TABLE hdiextxgui (id INT, country STRING, hdi FLOAT, lifeex INT, mysch INT, eysch INT, gni INT) 
ROW FORMAT DELIMITED FIELDS TERMINATED BY ',' 
STORED AS TEXTFILE 
LOCATION '/user/hadoop/datasets/onu/hdi/'

-- Creamos la query a la tabla llamada 'hdiextxgui'
SELECT * FROM hdiextxgui LIMIT 10;

-- Tabla externa en S3: 
CREATE EXTERNAL TABLE hdiens3 (id INT, country STRING, hdi FLOAT, lifeex INT, mysch INT, eysch INT, gni INT) 
ROW FORMAT DELIMITED FIELDS TERMINATED BY ',' 
STORED AS TEXTFILE 
LOCATION 's3://bdatasets/onu/hdi'

-- Verificaos la creación de la tabla.
SHOW TABLES;

-- Creamos la query a la tabla llamada 'hdiens3'
SELECT * FROM hdiens3 LIMIT 10;

-- REALIZADO CON beeline.
SELECT country, gni FROM hdiens3 WHERE gni > 2000;

-- JOIN...
-- Crear la tabla EXPO:
CREATE EXTERNAL TABLE EXPO (country STRING, expct FLOAT) 
ROW FORMAT DELIMITED FIELDS TERMINATED BY ',' 
STORED AS TEXTFILE 
LOCATION 's3://bdatasets/onu/export';

-- Verificaos la creación de la tabla.
SHOW TABLES;

-- Creamos la query a la tabla llamada 'expo'
SELECT * FROM expo LIMIT 10;

-- EJECUTAR EL JOIN DE 2 TABLAS 'hdiens3' y 'expo':
SELECT h.country, gni, expct FROM hdiens3 h JOIN expo e ON (h.country = e.country) WHERE gni > 2000;
```

