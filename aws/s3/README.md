## Notas S3

Un archivo en S3 no puede pesar más de 5GB
Un objeto en S3 no puede pesar más de 5TB

### Policies
- Identity Policy: Permite a una entidad de esa misma cuenta de AWS acceder a recursos dentro de la misma.
~~~json
{
   "Version":"2012-10-17",
   "Statement":[
      {
         "Effect":"Allow",
         "Action": "s3:ListAllMyBuckets",
         "Resource":"*"
      },
      {
         "Effect":"Allow",
         "Action":["s3:ListBucket","s3:GetBucketLocation"],
         "Resource":"arn:aws:s3:::awsexamplebucket1"
      },
      {
         "Effect":"Allow",
         "Action":[
            "s3:PutObject",
            "s3:PutObjectAcl",
            "s3:GetObject",
            "s3:GetObjectAcl",
            "s3:DeleteObject"
         ],
         "Resource":"arn:aws:s3:::awsexamplebucket1/*"
      }
   ]
}
~~~

- Resource Policy: Permite a una entidad de esa misma cuenta de AWS acceder a un recurso, como lo son los objetos en S3.

- Bucket Policy: Permite a una entidad de cualquier cuenta en AWS acceder a un recurso.

*Ejemplo 1 (Permitiendo a todos)*
~~~json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicRead",
            "Effect": "Allow",
            "Principal": "*",
            "Action": [
                "s3:GetObject",
                "s3:GetObjectVersion"
            ],
            "Resource": [
                "arn:aws:s3:::DOC-EXAMPLE-BUCKET/*"
            ]
        }
    ]
}
~~~

*Ejemplo 2 (Solo permitiendo a un rango de ips)*
~~~json
{
    "Version": "2012-10-17",
    "Id": "S3PolicyId1",
    "Statement": [
        {
            "Sid": "IPAllow",
            "Effect": "Deny",
            "Principal": "*",
            "Action": "s3:*",
            "Resource": [
                "arn:aws:s3:::DOC-EXAMPLE-BUCKET",
                "arn:aws:s3:::DOC-EXAMPLE-BUCKET/*"
            ],
            "Condition": {
                "NotIpAddress": {
                    "aws:SourceIp": "54.240.143.0/24"
                }
            }
        }
    ]
}
~~~

### ACL
Administran el acceso hacia los buckets y objetos, es una forma de darle seguridad a una forma más general a los recursos. No es recomendable usarlas debido a que solo tienen dos formas de acceso, *lectura* y *escritura*.

### Block Public Access
Bloquea el acceso a todo el publico, está habilita de forma predeterminada, así es como AWS recomienda mantener nuestro acceso a los recursos. Si queremos agregar **bucket policies** debemos hacer habilitar el acceso a todo el publico y luego generar nuestra politica.

## Versionamiento de objetos
Permite tener un historial de versiones sobre los objetos.
Este versionamiento no se puede deshabilitar una vez ya habilitado, solo se puede suspender, es decir, pausar los registros de versionado de los objetos.

### MFA Delete
Multi-factor authentication delete. Capa de seguridad extra, que solo está disponible si el versionamiento está activado.

### PUT OBJECT (API)

#### Single Put Upload
- Brinda un único flujo de datos hacia S3
- Si el envio de datos falla, la carga falla
- Requiere reenviar todo el objeto nuevamente
- Velocidad y fiabilidad limitada a 1 stream
- Cualquier subida de objeto no debe ser mayor a 5 GB

#### Multipart Put Upload
- Los datos son divididos o fragmentados
- El tamaño mínimo del objeto o datos debe ser de 100 MB para usar esta característica
- Una carga de datos a S3 puede ser dividida en un máximo de 10 mil partes y cada fragmento puede tener un tamaño entre 5 MB y 5 GB
- La última parte dividida es sobrante por lo que puede ser menor a 5 MB
- Cada parte dividida es una parte aislada en la carga de los datos
- Si una parte dividida falla, esta puede ser resubida sin afectar a las demas