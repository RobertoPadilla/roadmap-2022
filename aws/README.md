# AWS Fundaments

## Elastic Beanstalk:
Es un modelo de arquitectura provisionado por AWS el cual permite auto escalar nuestra aplicación simplemente subiendo nuestro código.

## EC2
Es una computadora virtual con recursos que nosotros especificamos.

## Lambda
Un servicio serverless de amazon, el cual nos permite ejecutar un pedazo de código sobre peticion, este proceso gestiona los recursos de manera automatica. Nos permite seleccionar el lenguaje que necesitemos y solamente queda subir nuestro código.

## Cloud Watch
Sistema de métricas. Se muestra graficamente el estado de nuestra arquitectura y de todos nuestros servicios. También permite configurar alarmas relacionadas a nuestros servicios.
Otra funcion de este servicio es registrar logs de nuestras aplicaciones e instancias.

## Cloud Trail
Herramienta que permite registrar la actividad de los usuarios IAM en la consola de amazon.

## ACM
Administrador de certificados SSL/TLS. Esta herramienta permite registrar servicios con estos certificados, pero no gratuitamente para todos ellos, solo para Elastic Load Balancing (ELB) Amazon CloudFront, Cognito, Elastic Beanstalk, App Runner, API Gateway, Nitro Enclaves y CloudFormation (05/01/2022)

## GuarDuty
AWS permite que hagas una auditoria constante de todos los intentos de conexiones que tienen tus equipos de computo. En pocas palabras, registrar nuestros servicios buscando ataques informaticos, alertandonos para tomar medidas.

## REkognition
Servicio de IA que permite escanear fotografias en busca de cualquier parametro

## S3
Almacenamiento de archivos. Permite ser consultado a través de endpoints, pueden ser respaldados y versionados. También permite restringir el acceso al contenido.

- Glacier: Almacenamiento más economico pero más lento. Es buena opcion para archivos que deban ser guardados y que no se utilizen continuamente

## RDS
Relational Database Service. Brinda múltiples opciones para gestionar bases de datos relacionales MySQL y Postgres. 

- Aurora: Este servicio es un intento de Amazon de optimizar el performance de las bases de datos relacionales. Son recomendables debido a esto. La velocidad aumenta y el rendimiento en general.

## Route 53
Permite modificar y administrar el DNS, registrar o transferir dominios, crear subdominios

## IAM
Permite gestionar los usuarios que acceden a la consola de AWS.



---

# Tools

## Calculator
Amazon calculator [here](https://calculator.aws/).
