## Util commands

### Config

~~~bash
aws configure # Crear o editar un perfil default
~~~
~~~bash
# Editar o crear un perfil en la consola
aws configure --profile <my-profile>
~~~

### S3

Si nuestros recursos están protegidos por politicas de acceso, al final del comando siempre se deberá colocar el perfil que tenga acceso a esos recursos, como se muestra en el primer ejemplo.

Subir un archivo a nuestro bucket (al final del comando se coloca el perfil que puede acceder al recurso)
~~~bash
# puede ser bidireccional
aws s3 cp "localsource" s3://<my-bucket> --profile <my-profile>
~~~
Listar nustros recursos en S3
~~~bash
aws s3 ls
~~~
Listar nustros recursos dentro de un bucket
~~~bash
aws s3 ls s3://<my-bucket>
~~~
Convertir un bucket a una página web estatica
~~~bash
aws s3 website s3://<my-bucket> --index-document index.html --error-document error.html
~~~
Generar una PreSigned Url
~~~bash
aws s3 presign s3://<my-bucket>/<object> --expires-in <time-in-sec> --profile <my-profile>
~~~