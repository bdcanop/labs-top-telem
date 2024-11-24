# Laboratorio 3-0 

## Creamos un Cluster con las siguientes configuraciones

#### Para crear el cluster buscamos EMR en aws, seleccionamos crear cluster y seguimos las siguientes configuraciones

![Pasted Graphic 3](https://github.com/user-attachments/assets/2f919a09-608e-4ba4-8a0d-4aed5832ca83)

![Pasted Graphic 4](https://github.com/user-attachments/assets/0c5c9f1d-f9be-49ce-8662-b49cf928a2e6)

![Pasted Graphic 5](https://github.com/user-attachments/assets/3d62634d-0594-420f-807f-5ce40dff8775)

![Pasted Graphic 6](https://github.com/user-attachments/assets/26fe5cd1-7f64-4b71-b423-8aa49e634151)

![Pasted Graphic 7](https://github.com/user-attachments/assets/45fe06a4-e75e-4943-a588-230f6a93bdb8)

#### Luego le damos a crear cluster y veremos el mensaje de que ha sido creado

![Pasted Graphic 8](https://github.com/user-attachments/assets/4bc56825-602b-4455-a12a-823efa1beeb0)

#### Luego deberemos abrir todos los puertos TCP, para ello vamos a block public access, seleccionamos turn off y guardamos los cambios (esto sólo se hace una vez)

#### También debemos abrir los puertos de las aplicaciones hadoop/spark en el security group del nodo master 

#### Aquí vemos que son las que están en el puerto 8888, 9443 y 8890

![Pasted Graphic 10](https://github.com/user-attachments/assets/66cd4306-addd-4b11-8be0-18fecc3c5781)

####  Además debemos abrir también los puertos 22, 14000 y 9870

Para ello vamos a la instancia del nodo master en EC2, luego a grupo de seguridad y editamos las reglas de entradas agregando las reglas para cada puerto

![Pasted Graphic 11](https://github.com/user-attachments/assets/22f66828-9480-48c3-9cbf-20138136a456)

![Pasted Graphic 9](https://github.com/user-attachments/assets/1f4f6a7b-a69e-4831-9cef-a3bdec482661)

#### Ahora podremos acceder a las aplicaciones

Vamos al EMR, entramos a las aplicaciones y específicamente a hadoop, el nombre de usuario debe ser hadoop y la contraseña puede ser cualquiera

![Pasted Graphic 12](https://github.com/user-attachments/assets/dd3e3a76-9955-4b46-9052-5ccc46928eac)

#### Vemos que tenemos acceso 

![Pasted Graphic 13](https://github.com/user-attachments/assets/cbaf4400-2fcf-490b-93a7-ef76ebcdf2e8)

#### También podemos acceder a la aplicación de jupyterhub con usuario jovyan y contraseña jupyter

![Pasted Graphic 14](https://github.com/user-attachments/assets/b2478acd-6f4e-4c1d-b600-ac8a9f303633)

![Pasted Graphic 15](https://github.com/user-attachments/assets/d08be663-e31d-49e2-abf1-759c1a1d5ede)

![Pasted Graphic 16](https://github.com/user-attachments/assets/99d77bbe-bb12-4a04-bc0b-fbe4ae1d0afa)

