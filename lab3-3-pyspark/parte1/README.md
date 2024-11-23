# Parte 1

## Ingresamos a PySpark

<img width="1440" alt="Pasted Graphic 38" src="https://github.com/user-attachments/assets/cedc079f-9655-4484-ae6e-751612667ad0">

## Cargamos los archivos desde HDFS

#### Para cargar los archivos usamos:

```
files_rdd = sc.textFile("hdfs:///user/hadoop/datasets/gutenberg-small/*.txt")
```

#### Para separar las palabras y contar las ocurrencias usamos: 

```
wc_unsort = files_rdd.flatMap(lambda line: line.split()).map(lambda word: (word, 1)).reduceByKey(lambda a, b: a + b)
```

#### Para ordenar las palabras usamos:

```
wc = wc_unsort.sortBy(lambda a: -a[1])
```

#### Y para mostrar las 10 palabras más frecuentes usamos:

```
for tupla in wc.take(10):
    print(tupla)
```


<img width="1440" alt="Pasted Graphic 39" src="https://github.com/user-attachments/assets/7ca8f00c-0918-4c20-85ff-9f1744c03a20">

#### Podemos guardar el resultado como múltiples archivos RDD:

```
wc.saveAsTextFile("hdfs:///tmp/wcout1")
```

#### Consolidamos el resultado en un solo archivo:

```
wc.coalesce(1).saveAsTextFile("hdfs:///tmp/wcout2")
```

#### Y ya podemos salir:

`exit()`


<img width="1440" alt="Pasted Graphic 40" src="https://github.com/user-attachments/assets/ae284e89-c77c-4248-b524-93939f164cfc">


#### Podemos verificar la creación de los archivos: 

```
hdfs dfs -ls hdfs:///tmp/
```

## Como un archivo

#### Creamos el archivo:

```
touch wc-pyspark-daniel.py
```

#### Editamos el archivo, en este caso con nano:

```
nano wc-pyspark-daniel.py
```

<img width="1440" alt="Pasted Graphic 42" src="https://github.com/user-attachments/assets/e77b78d6-1b7a-4c70-b80e-b78a2e773f66">

#### Pegamos el siguiente contenido adaptados a nuestro caso:

```
from pyspark.sql import SparkSession

# puede no necesitar instanciar las variables spark y sc si esta ejecutando en AWS EMR:
spark = SparkSession.builder.appName("WordCount").getOrCreate()
sc = spark.sparkContext

files_rdd = sc.textFile("s3://emontoyadatasets/gutenberg-small/*.txt")
#files_rdd = sc.textFile("hdfs:///datasets/gutenberg-small/*.txt")
wc_unsort = files_rdd.flatMap(lambda line: line.split()).map(lambda word: (word, 1)).reduceByKey(lambda a, b: a + b)
wc = wc_unsort.sortBy(lambda a: -a[1])
wc.coalesce(1).saveAsTextFile("hdfs:///tmp/wcout1")
```

<img width="1440" alt="Pasted Graphic 41" src="https://github.com/user-attachments/assets/6bc328d5-0fbe-4b16-b891-a69f9cfbe50c">

#### Ahora podremos ejecutar el archivo:

```
spark-submit --master yarn --deploy-mode cluster wc-pyspark-daniel.py
```

<img width="1440" alt="Pasted Graphic 44" src="https://github.com/user-attachments/assets/2e63a51b-6a88-43a8-a167-df019fea880c">

#### Verificamos la creación de los archivos

```
hdfs dfs -ls hdfs:///tmp/
```

<img width="1440" alt="Pasted Graphic 43" src="https://github.com/user-attachments/assets/6ac4ac63-68a2-4678-bddb-e421a3ac5c49">

## Desde Zeppelin

#### Ingresamos a Zeppelin y creamos un notebook

<img width="1440" alt="Pasted Graphic 45" src="https://github.com/user-attachments/assets/8efa08b9-5260-40e6-9f1f-a7cff7aa17f2">

#### cramos el notebook dentro de la carpeta que escojamos y seleccionamos spark

<img width="1440" alt="Pasted Graphic 46" src="https://github.com/user-attachments/assets/f5f8f927-5601-4f92-8574-478d972e454f">

#### copiamos el siguiente contenido

```
    %spark2.pyspark
    # WORDCOUNT COMPACTO
    #files_rdd = sc.textFile("s3://emontoyadatasets/gutenberg-small/*.txt")
    files_rdd = sc.textFile("hdfs:///datasets/gutenberg-small/*.txt")
    wc_unsort = files_rdd.flatMap(lambda line: line.split()).map(lambda word: (word, 1)).reduceByKey(lambda a, b: a + b)
    wc = wc_unsort.sortBy(lambda a: -a[1])
    for tupla in wc.take(10):
        print(tupla)
    wc.coalesce(1).saveAsTextFile("hdfs:///tmp/wcout1")
```

<img width="1440" alt="Pasted Graphic 47" src="https://github.com/user-attachments/assets/3f1d49e4-c4cb-4243-9865-909f964966bd">

#### Si lo ejecutamos podremos ver el resultado

<img width="1440" alt="Pasted Graphic 48" src="https://github.com/user-attachments/assets/dc21a0cd-ddc2-482a-b73a-83da9808946a">

#### Verificamos la creación del archivo en la instancia

<img width="1440" alt="Pasted Graphic 49" src="https://github.com/user-attachments/assets/210c86d0-51c6-4b20-ac2e-0283e9f2e1a1">

## Desde Jupyter Notebooks

#### Importamos el siguiente notebook en jupyter

[wordcount-spark.ipynb](lab3-3-pyspark/parte1/README.md)

<img width="1440" alt="Pasted Graphic 50" src="https://github.com/user-attachments/assets/6486c588-0f41-4150-96a1-e9f1b47af39c">

#### Ejecutamos las celdas

<img width="1440" alt="Pasted Graphic 51" src="https://github.com/user-attachments/assets/7c3d58a5-6ece-4a13-b031-c62850e964dd">

<img width="1440" alt="Pasted Graphic 52" src="https://github.com/user-attachments/assets/d0855b89-f2f8-4334-aaf3-34cefedf3706">

<img width="1440" alt="Pasted Graphic 53" src="https://github.com/user-attachments/assets/0c07e31e-14c0-4e0a-83d0-78cbf8bd6872">

#### Verificamos la creación del archivo desde jupyter en la instancia

```
hdfs dfs -ls hdfs:///tmp/
```

<img width="1440" alt="Pasted Graphic 54" src="https://github.com/user-attachments/assets/f81baf03-2085-4cfe-8d2d-12f5b49d840f">

#### También podemos ver los resultados por GUI en el s3

<img width="1440" alt="Pasted Graphic 55" src="https://github.com/user-attachments/assets/9b91f762-7dca-42fb-9f68-3b0e5496eb6b">

# Parte 2

#### La parte 2 la podemos encontrar en el siguiente link:

[Parte 2](../parte2/README.md)

