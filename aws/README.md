# AWS Fundaments

## Elastic Beanstalk:
Es un modelo de arquitectura provisionado por AWS el cual permite auto escalar nuestra aplicación simplemente subiendo nuestro código.

## EC2
Es una computadora virtual con recursos que nosotros especificamos.

Descripción de nombres de instancias EC2:
- primera posicion: letra que define la clase de familia
- segunda posicion: numero que acompaña a la familia, este numero representa la generacion de el tipo de familia
- tercera posicion(no siempre existe): letra que representa una mejora sobre previas versiones de esta familia y esta generación. 
    - Si es una letra "g" es por que la instancia está construida con el procesador de Amazon "Graviton2". ej R6g.
    - Si es una letra "a" es por que trabaja con AMD. ej. R5a.
    - Si es una letra "n" es por que trabaja con un procesador Xeon 2nd Generacion. ej R5n.
- descripcion despúes del punto: tamaño de caracteristicas de hardware (RAM, CPU, TARJETA DE RED) el almacenamiento no está incluido ya que este se puede incrementar por aparte.

Tipos de instancias:
- General Purpose
- Compute Optimized
- Memory Optimized
- Accelerated Computing
- Storage Optimized

Estrategias de costo:
- On-Demand: Paga por lo que se consume. Inicia/Termina según necesidad.
- Spot Instances: Ahorra hasta un 90% en comparación de On-Demand. Su principal caracteristica es que puede que se interrumpan debido a una especie de subasta, depende de la demanda actual de ese servicio de AWS.
- Reserved instances (RI): Ahorra hasta un 75% en comparación al precio On-Demand. Se hace un contrato para reservar una instancia minimo por un año, el pago es flexible, se puede pagar en diferentes modalidades.
    - Standars RI: Estos proporcionan el descuento más significativo (hasta un 72% de descuento bajo demanda) y son los más adecuados para el uso en estado estable. (Si no se ocupa la capacidad de cómputo ni el tiempo especificado, aún así amazon cobrará por todo el tiempo predefinido)
    - Convertible RI: (hasta un 54% de descuento bajo demanda) Ofrece la capacidad de cambiar los atributos de la instancia reservada siempre que el intercambio dé como resultado la creación de instancias reservadas de igual o mayor valor. Este se paga al final para calcular los costos extras si es que se modificó la familia de la instancia.
    - Scheduled RI: Estos permiten reservar instancias por un tiempo aún más determinado, una semana, un més o un día.
- Saving Plans: A diferencia de los RI, estos planes son más flexibles en cuanto al uso de la capacidad de computo.
- Dedicated Host: Un servidor fisico dedicado. Se puede obtener un 70% de descuento reservandolo.

### Auto Scaling Groups (ASG)
Servicio para aumentar y decrementar capacidad de computo de manera horizontal automaticamente.
~~~txt
Minimum size: 1
Desired capacity: 2
Maximum size: 4
~~~
- Minimun size: Tamaño de instancias minimas a las que podemos permitirnos llegar.
- Desired capacity: Tamaño deseado para ofrecer a nuestros clientes.
- Maximum size: Tamaño de instancias máximas que podemos permitirnos tener.

#### Scaling Policies
Manual: Hacer todo el escalado de forma manual con los LT.
Squeduled: Programar en el tiempo el estado de escalamiento.
Dynamic: Dependiendo el estado de las instancias se escalan automaticamente.

### Launch Template
Plantilla para lanzar rápidamente una instancia preconfigurada o usar el servicio de ASG. (Se recomienda usar esta herramienta en lugar de Launch configuration)

### Launch Configuration
Principalmente sirven para la configuración de ASG.

### Elastic Load Balancer (ELB)
Servicio que brinda Alta Disponibilidad, distibuyendo la carga de solicitudes entre diferentes instancias para no saturar una sola de estas.

Se distribuyen en 2 zonas de disponibilidad, esto con el fin de aumentar la disponibilidad de nuestra aplicacion, esto por el motivo de: si una zona de disponibilidad se cae, tener disponible la aplicacion en otra zona.

Tipos:
- Classic: Primer tipo de balanceador que surgió. Pronto en desuso. Aplicable para TCP y HTTP.
- Application Load Balancer (ALB): Opera sobre el modelo OSI trabaja sobre la capa 7 y es aplicable para HTTP/HTTPS. Inteligente.
- Network Load Balancer (NLB): Ofrecen IP Fija sin importar las zonas de disponibilidad configuradas. Aplicable para TCP. Trabaja sobre la capa 4 del modelo OSI. Alto rendimiento.

## VPC (Virtual Private Cloud)
Aislamiento de una parte lógica de la infraestructura de Amazon.

Tiene las siguientes caracteristicas:
- Subnet
- Route Table
- Internet Gateway
- Network ACL (NACL)
- Security Group (SG)
- NAT (Gateway o Instance) # Servicio administrado que es cobrado.
## Lambda
Un servicio serverless de amazon, el cual nos permite ejecutar un pedazo de código sobre peticion, este proceso gestiona los recursos de manera automatica. Nos permite seleccionar el lenguaje que necesitemos y solamente queda subir nuestro código.

## CloudShell
Brinda el servicio de AWS CLI mediante una interfaz web.

## SNS
Servicio de mensajeria administrado por AWS.

Permite la comunicacion de Aplicacion a Aplicacion (A2A) y de Aplicacion a Persona (A2P).

Permite notificaciones a un dispositivo movil con Notificaciones push, correo electronico y SMS.

## AWS Config
Servicio que permite examinar todo el comportamiento dentro de la cuenta de AWS.

Permite:
- Evaluar las configuraciones de los recursos (Arrojan niveles de Cumplimiento - Incumplimiento). Sirver para cumplir con normas de seguridad.
- Responde a cambios en las configuraciones y relaciones de los recursos que no se hayan autorizado (registro de movimientos por usuario).
- Evaluacion continua.
- Administracion de cambios.
- Monitoreo de conformidad en toda la compañia.

## Cloud Watch
Sistema de métricas. Se muestra graficamente el estado de nuestra arquitectura y de todos nuestros servicios. También permite configurar alarmas relacionadas a nuestros servicios.
Otra funcion de este servicio es registrar logs de nuestras aplicaciones e instancias.

Posibles configuraciones:
- Alarmas
- Métricas
- Eventos

Tipos de monitoreo:
- Básico (Gratis y por default registros cada 5min)
- Detallado (Costo registros cada 60s)

## Cloud Trail
Herramienta que permite registrar la actividad de los usuarios IAM en la consola de amazon.

## CloudFront
Pemite acercar a usuarios alejados de la region donde se sirve tu aplicacion mediante puntos de precencia (PoP).
- Es un servicio CDN
- Almacena contenido en caché en PoP (Poin of Precense) más cercanos a los clientes.
- Baja latencia.
- Alto Rendimiento.
- Compatible para manejar contenido estático y dinámico.

Caracteristicas:
- Origin: Ubicación origin de tu contenido.
- Distribution: Tipo de configuración. Contenido estatico, dinamico o para streming.
- Edge Location: PoP.

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

- Aurora: Este servicio es un intento de Amazon de optimizar el performance de las bases de datos relacionales (compatible con MySQL y PostgreSQL). Son recomendables debido a esto. La velocidad aumenta junto al rendimiento en general.

## DMS (Data Migration Service)
Usado para migrar bases de datos relacionales on premise (montados por nosotros mismos) a servicios de AWS

## DynamoDB
Base de datos clave-valor y documentos, soporta +20 millones de solicitudes por segundo.

Usado para arquitecturas:
- Serverless
- Backend Moviles
- Microservicios

## Route 53
Permite modificar y administrar el DNS, registrar o transferir dominios, crear subdominios.

Caracteristicas:
- Hosted Zone: Registrar dominio - comprarlo o migrarlo. Pueden ser publicos (Internert) o privados (VPC).
- RecordSet: Son los subdominios.

## IAM
Permite gestionar los usuarios que acceden a la consola de AWS. Un usuario puede asociarse con 10 grupos como máximo en paralelo.

## AWS Shield
Brinda protección contra ataques DDoS. Brinda protección a nivel de la capa 4 del Modelo OSI.
- Shield Standard (Gratis y por default en la cuenta)
- Shield Advanced (Costo ~$3,000/mes):
    - Equipo de respuesta anti-incidentes
    - Disponible 24/7

## AWS WAF
Brinda protección contra ataques web. Brinda protección a nivel de la capa 7 del Modelo OSI. (Costo)

Reglas de WAF:
- Custom: Reglas personalizadas acorde a nuestro negocio
- Administradas por AWS: Reglas brindadas por AWS
- Brindadas por un vendor: Capacidad de contratar las reglas de otro proveedor en el marketplace de AWS.

## Amazon Inspector
Servicio automatico de evaluación de seguridad. Se ejecuta sobre instancias EC2 tanto Windows y Linux. (Capa gratuita)

## Amazon Macie
Es un servicio que nos brinda descubrimiento y protección de datos confidenciales. (Capa free)

Macie utiliza ML (Machine Learning) para poder evaluar los datos que tengas en buckets S3, y descubrir datos como:
- Numeros de tarjeta de creditos
- Contraseñas
- Keypair

## AWS KMS (Key Managment Service)
Permite crear y controlar las claves de cifrado de forma sencilla a traves de una amplia variedad de servicios AWS (Capa gratuita)

## AWS SSM
Brinda visibilidad y control para nuestra infraestructura AWS.

A traves de este servicio se puede administrar de forma operativa y automatica los recursos de AWS. (Capa gratuita)

## Trusted Advisor
Es una herramienta online que nos provee de asesoramiento en tiempo real ayudandonos en el aprovisonamiento de recursos con las mejores practicas recomendadas de AWS. *En pocas palabras son consejos que esta herramienta nos da día a día para mejorar la infraestructura del negocio.*

En general ayudan a optimizar la infraestructura aumentando el nivel de:
- Seguridad
- Rendimiento
- Ahorro de costos
- Tolerancia a fallos
- Limites de servicios
# Tools

## AWS CLI Builder
CLI Builder [here](https://awsclibuilder.com/home)

## Policy Generator
Policy Generator [here](https://awspolicygen.s3.amazonaws.com/policygen.html)

## Calculator
Amazon calculator [here](https://calculator.aws/).

## AWS Accelerated Transfer Tool (General)
[Tool](http://s3-accelerate-speedtest.s3-accelerate.amazonaws.com/en/accelerate-speed-comparsion.html)
## AWS Accelerated Transfer Tool (Personalized)
[Tool](https://s3-accelerate-speedtest.s3-accelerate.amazonaws.com/en/accelerate-speed-comparsion.html?region=COLOCARAQUILAREGION&origBucketName=COLOCARAQUINOMBREBUCKET) *(Cambiar los parametros marcados en mayusculas)*