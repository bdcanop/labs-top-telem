# Laboratorio 3-1

#### Una vez en la instancia del nodo principal lo primero que debemos hacer es instalar git y clonar el repositorio

Para ello usamos el comando 

```
sudo yum install git
```

Y procedemos con la instalación 

<img width="1440" alt="Pasted Graphic 9" src="https://github.com/user-attachments/assets/ef96f1e1-56be-4a44-bf1a-76fbff63d85a">

Luego clonamos el repositorio usando el comando 

```
git clone https://github.com/st0263eafit/st0263-242.git
```

<img width="1440" alt="Pasted Graphic 10" src="https://github.com/user-attachments/assets/ab77c576-bdd2-401b-9f0a-b991bb10e808">


Creamos el directorio datasets en hadoop

```
hdfs dfs -mkdir /user/hadoop/datasets
```

Y dentro del directorio gutenberg-small

```
hdfs dfs -mkdir /user/hadoop/datasets/gutenberg-small
```

Luego pasamos los archivos terminados en .txt que están en la carpeta gutenberg-small del repositorio a la carpeta que recién creamos

```
hdfs dfs -put /home/hadoop/st0263-242/bigdata/datasets/gutenberg-small/*.txt /user/hadoop/datasets/gutenberg-small/
```

Y verificamos el contenido de esta

```
hdfs dfs -ls /user/hadoop/datasets/gutenberg-small/
```

<img width="1440" alt="Pasted Graphic 11" src="https://github.com/user-attachments/assets/ee1899fc-1fd7-4fd1-ac69-c1c3e9f71d66">

Luego creamos una carpeta, en este caso llamada mis_datasets

```
mkdir mis_datasets 
```

Descargamos usando el método get el contenido de gutenberg-small en la carpeta local que acabamos de crear

```
hdfs dfs -get /user/hadoop/datasets/gutenberg-small/* ~hadoop/mis_datasets/
```

<img width="1440" alt="Pasted Graphic 12" src="https://github.com/user-attachments/assets/43e4f310-133c-4078-a0ad-6a628fb308c3">

También hay varios comandos de hdfs que se pueden usar para distindos propósitos 

```
du <path>             uso de disco en bytes
mv <src> <dest>       mover archive(s)
cp <src> <dest>       copiar archivo(s)
rm <path>             borrar archive(s)
put <localSrc> <dest-hdfs> copiar local a hdfs
cat <file-name>       mostrar contenido de archivo
chmod [-R] mode       cambiar los permisos de un archivo
chown <username> files   cambiar el dueño de un archivo
chgrp <group> files      cambiar el grupo de un archivo
```

#### También podemos hacerlo por la interfaz de hue

Para ello nos dirigimos a la sección de files

<img width="1440" alt="Pasted Graphic 13" src="https://github.com/user-attachments/assets/6ea89379-4824-423f-b557-78fe4a5db2ff">

Damos click en el botón new y seleccionamos directory 

<img width="1440" alt="Pasted Graphic 14" src="https://github.com/user-attachments/assets/9d4a0002-ef9e-4699-bb38-967ee3bafec2">

Le ponemos nombre al directorio y le damos create

<img width="1440" alt="Pasted Graphic 15" src="https://github.com/user-attachments/assets/a91e75c3-e1f1-49fd-8405-e33ef0b85299">

Dentro de este, crearemos otro directorio llamado onu

<img width="1440" alt="Pasted Graphic 16" src="https://github.com/user-attachments/assets/18353e31-ba35-40e4-a8a8-c34efe6b330c">

Y subiremos archivos usando el botón upload y luego select files para seleccionar los archivos que querramos subir

<img width="1440" alt="Pasted Graphic 17" src="https://github.com/user-attachments/assets/505b5468-0ac3-4cc5-99f7-0f2dae609345">

Escojemos los archivos y le damos open para subirlos

<img width="1440" alt="Pasted Graphic 18" src="https://github.com/user-attachments/assets/920c0a0d-573f-4097-b1db-3661fb688611">

Podemos ver que se subieron los archivos con éxito

<img width="1440" alt="Pasted Graphic 19" src="https://github.com/user-attachments/assets/4e371b25-ab3a-44f1-8b69-b7a2bb2d5629">

E incluso podemos ver el contenido de estos 

<img width="1440" alt="Pasted Graphic 20" src="https://github.com/user-attachments/assets/499618da-27c4-4c47-97f0-2084c05aeb06">

