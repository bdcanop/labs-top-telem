# Parte 2

#### Copiamos los datos de Covid19 en el s3 en este caso en la carpeta lab4-covid19

<img width="1440" alt="Pasted Graphic 56" src="https://github.com/user-attachments/assets/cfe2bdca-d45d-4c7f-a4df-eb7964dfd6af">

#### Para la parte de jupyterhub ingresamos al jupyter e importamos el siguiente template:

[Data_processing_using_PySpark.ipynb](./Data_processing_using_PySpark.ipynb)

<img width="1440" alt="Pasted Graphic 59" src="https://github.com/user-attachments/assets/a83e2c41-59fe-42bf-9547-d8d8b6f79cda">

<img width="1440" alt="Pasted Graphic 57" src="https://github.com/user-attachments/assets/196a806b-f193-45c3-92f0-f1fea1412249">

<img width="1440" alt="Data Processing using Pyspark" src="https://github.com/user-attachments/assets/89b32711-953e-4d48-a51e-90d9915bc973">

#### También los cargamos en Google Colab

<img width="1419" alt="Pasted Graphic 74" src="https://github.com/user-attachments/assets/f64fdfe9-22a0-48ec-9fe6-bd4472e93de0">

#### Procesamos los datos en jupyter hub y lo guardamos en el s3

<img width="1419" alt="Pasted Graphic 72" src="https://github.com/user-attachments/assets/0a38870d-ad4b-452e-853a-623feee60955">

#### Procesamos los datos en google colab y los guardamos en el drive

<img width="1419" alt="Pasted Graphic 75" src="https://github.com/user-attachments/assets/67767f80-6cd8-4e21-8d87-3ca7031de0b4">

#### Podemos ver el resultado de los datos procesados en jupyterhub

<img width="1419" alt="Pasted Graphic 73" src="https://github.com/user-attachments/assets/1903b1d4-e26d-44b9-89c0-5db793cde13f">

#### Y podemos ver el resultado de los datos procesados en el drive

<img width="1419" alt="Pasted Graphic 76" src="https://github.com/user-attachments/assets/064fe2f8-9900-47ec-8eaf-6058d5a1a133">

#### Los notebooks terminados se pueden encontrar en los siguientes links:

[Notebook Google Colab - Drive](../Solucion_Colab_Data_processing_using_PySpark.ipynb)

[Notebook JupyterHub](../Solucion_Jupyter_Data_processing_using_PySpark.ipynb)

#### Puede encontrar la uri de los datos procesados y sin procesar aquí:

uri de los datos sin procesar: s3://lab4-covid19/Raw/Covid19-Colombia.csv

uri de los datos procesados: s3://lab4-covid19/Refined/dfjupyter/part-00000-6c0e1f35-6f26-4eb9-9799-caec006bdc2b-c000.csv

[URL de los datos sin procesar](https://lab4-covid19.s3.us-east-1.amazonaws.com/Raw/Covid19-Colombia.csv)

[URL de los datos procesados](https://lab4-covid19.s3.us-east-1.amazonaws.com/Refined/dfjupyter/part-00000-6c0e1f35-6f26-4eb9-9799-caec006bdc2b-c000.csv)
