# AWS Fundaments

## Elastic Beanstalk:
Es un modelo de arquitectura provisionado por AWS el cual permite auto escalar nuestra aplicación simplemente subiendo nuestro código.

## EC2
Es una computadora virtual con recursos que nosotros especificamos.

## Lambda
Un servicio serverless de amazon, el cual nos permite ejecutar un pedazo de código sobre peticion, este proceso gestiona los recursos de manera automatica. Nos permite seleccionar el lenguaje que necesitemos y solamente queda subir nuestro código.

## CloudShell
Brinda el servicio de AWS CLI mediante una interfaz web.

## Cloud Watch
Sistema de métricas. Se muestra graficamente el estado de nuestra arquitectura y de todos nuestros servicios. También permite configurar alarmas relacionadas a nuestros servicios.
Otra funcion de este servicio es registrar logs de nuestras aplicaciones e instancias.

## Cloud Trail
Herramienta que permite registrar la actividad de los usuarios IAM en la consola de amazon.

## ACM
Administrador de certificados SSL/TLS. Esta herramienta permite registrar servicios con estos certificados, pero no gratuitamente para todos ellos, solo para Elastic Load Balancing (ELB) Amazon CloudFront, Cognito, Elastic Beanstalk, App Runner, API Gateway, Nitro Enclaves y CloudFormation (05/01/2022)

## GuarDuty
AWS permite que hagas una auditoria constante de todos los intentos de conexiones que tienen tus equipos de computo. En pocas palabras, registrar nuestros servicios buscando ataques informaticos, alertandonos para tomar medidas.

## Rekognition
Servicio de IA que permite escanear fotografias en busca de cualquier parametro

## S3
Almacenamiento de archivos. Permite ser consultado a través de endpoints, pueden ser respaldados y versionados. También permite restringir el acceso al contenido.

- S3 Standar: Uso de proposito general. (Más caro)
- S3 Intellingent-Tiering: Optimiza costos automáticamente moviendo la data a la clase más rentable
- S3 Standard-IA: Se usa con datos a los que se obtiene acceso con menos frecuencia, pero que requieren un acceso rápido cuando es necesario.
- S3 One Zone-IA: Similar al Standard-IA con la diferencia que opera en una sola zona de disponibilidad. (Si algo pasa con esa zona, el archivo se perdió)
- S3 Glacier: Almacenamiento más economico pero más seguro y duradero. Es buena opcion para archivos que deban ser guardados y que no se utilizen continuamente. El acceso a estos datos conlleva un tiempo de espera mayor (hasta 12 hrs)
- S3 Glacier Deep Archive: Retención a largo plazo. Esta forma de almacenamiento es recomendable para archivos a los que se accedan una o dos veces al año. (Disponibilidad de hasta 48 hrs)

## EBS (Elastic Block Storage)
Sistema de volúmenes (Unidades de disco) a diferencia del almacenamiento en S3 (objetos), este sistema almacena los datos en bloques. Está diseñado para usarse con instancias EC2.
Tienen alta durabilidad, disponibilidad y permiten el escalamiento del almacenamiento de forma sencilla.

***IOPS: Input Output Per Second***

- Basado en SSD:
    - gp2: EBS General Purpose SSD - Equilibria el rendimiento del precio para una amplia variedad de cargas de trabajo transaccionales.
    - io1: EBS Provisioned IOPS SSD - Diseñado para cargas de trabajo transaccionales sensibles a la latencia.
    - io2: EBS Provisioned IOPS SSD - Diseñado para aplicaciones sensibles a la latencia críticas para la empresa
- Basado en HDD:
    - st1: Throughput Optimized HDD - Diseñado para cargas de trabajo de alto rendimiento a las que se accede con frecuencia
    - sc1: Cold HDD - Diseñado para cargas de trabajo a las que se accede con menos frecuencia (por lo que es más rentable)

## EFS (Elastic File System)
Sistema de almacenamiento de archivos de alto rendimiento y escalabilidad. (~0,08 por GB). Baja latencia.

Permite que las aplicaciones alcancen niveles elevados de rendimiento.
- EFS Standard
- EFS IA: Es la más rentable.
## RDS
Relational Database Service. Brinda múltiples opciones para gestionar bases de datos relacionales MySQL y Postgres. 

- Aurora: Este servicio es un intento de Amazon de optimizar el performance de las bases de datos relacionales. Son recomendables debido a esto. La velocidad aumenta y el rendimiento en general.

## Route 53
Permite modificar y administrar el DNS, registrar o transferir dominios, crear subdominios

## IAM
Permite gestionar los usuarios que acceden a la consola de AWS.


# Tools

## AWS CLI Builder
CLI Builder [here](https://awsclibuilder.com/home)

## Policy Generator
Policy Generator [here](https://awspolicygen.s3.amazonaws.com/policygen.html)

## Calculator
Amazon calculator [here](https://calculator.aws/).

## AWS Accelerated Transfer Tool (General)
Tool [here](http://s3-accelerate-speedtest.s3-accelerate.amazonaws.com/en/accelerate-speed-comparsion.html)
## AWS Accelerated Transfer Tool (Personalized)
Tool [here](https://s3-accelerate-speedtest.s3-accelerate.amazonaws.com/en/accelerate-speed-comparsion.html?region=COLOCARAQUILAREGION&origBucketName=COLOCARAQUINOMBREBUCKET) *(Cambiar los parametros marcados en mayusculas)*