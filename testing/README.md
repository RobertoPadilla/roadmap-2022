# Testing

## Etapas
1. Planificación
    - Alcances y riesgos
    - Objetivos de pruebas
    - Tipos de pruebas
    - Recursos, condiciones
2. Análisis y diseño
    - Revisión de documentos
    - Condiciones de pruebas
    - Diseños de casos de pruebas
    - Entorno
    - Herramientas
3. Ejecución de pruebas
    - Finalización de casos de pruebas
    - Diseño de timeline (prototipos)
    - Ejecución
    - Resultados
    - Informe (Mencionar si existen errores o no)
    - Repetición (Si existen errores)
4. Evaluación de criterio de salida
    - Comparación de evidencia de pruebas (si nuestros criterios fueron satisfactorios)
    - Resumen para stakeholders
5. Actividades de cierre
    - Recolección de información de pruebas completadas
    - Documentacion de casos de pruebas (exitosos o no) y bugs encontrados

## Tipos de pruebas
![Piramide de Tests](https://www.campusmvp.es/recursos/image.axd?picture=/2020/2T/piramide.png)

### Pruebas unitarias
Son las pruebas que se realizan sobre un determinado módulo del sistema, independientemente de los demás. El objetivo es asegurar que cada modulo funcione correctamente por separado y fácilitar las pruebas de integración.

Caracteristicas:
- Demuestra buen estado del código.
- Aumentan la legibilidad del código.
- Sirven como documentación.
- Ejecución muy rápida.
- Cuando se refactoriza hay garantía de un correcto funcionamiento.
- Mejora la calidad del código.

### Pruebas de integración
Son las pruebas en las que se verifica que los diferentes sistemas de un mismo producto interactuan correctamente entre ellos. Se realizan y ejecutan después de las pruebas unitarias con el fin de encontrar errores en la comunicación entre ellas.

### Pruebas de sistema o E2E (end to end)
Simulación de interacción del cliente con nuestra aplicación (Automatizar el movimiento del mouse, input del teclado, etc). Se realizan después de las pruebas de integración y el objetivo es comprobar la funcionalidad de extremo a extremo. Está más orientada a asegurar que el comportamiento sea correcto en cada uno de los casos de uso del lado del cliente.

### Pruebas de aceptación
Se ejecutan una vez que el producto está terminado. Y su objetivo es que el cliente obtenga el resultado que se deseaba.

## Pruebas Funcionales y no Funcionales
### Funcionales
Se basa en un sistema ya hecho al que se le tiene que aplicar testing.
- Pruebas exploratorias: Ejecutar las pruebas a medida que se piensa en ellas (¿que pasa si hago esto en el código?)
- Pruebas de regresión: Pensadas para evitar el efecto onda en un producto estable en el momento de introducir un cambio (es ideal cada que se modifica el código)
- Pruebas de compatibilidad de entorno: Se prueba el mismo producto en diferentes entornos, con el objetivo de asegurar que se comporte igual en cada uno de ellos (ej. probar una web en diferentes navegadores o un programa de escritorio en diferentes sistemas operativos)
- Pruebas libres: Se ejecutan sin un plan de test. El desarrollador es libre de hacer las pruebas que crea necesarias.
- Pruebas de humo: Se asegura que no tenga defectos que interrumpa el funcionamiento básico del software y permita al desarrollador mejorar el proceso de testing para futuras entregas.
- Pruebas de sanidad: Más comunes, se encargan de verificar que una funcionalidad crítica cumpla su objetivo sin fallos.

### No funcionales
No están relacionados directamente con las funciones que realiza el sistema, están relacionadas con los diferentes complementos que acompañan al sistema como el entorno o el diseño.
- Pruebas de rendimiento: Verifica el comportamiento del sistema frente a un crecimiento de carga de consultas (estrés testing)
- Pruebas de backup: Verifica los procedimientos anti-fallos. Aseguramos que estos procedimientos no fallen.
- Pruebas de instalación: Verifica todo lo relacionado con el despliegue de producto (Documentación, instalacion, configuracion, post-instalacion, etc).
- Pruebas estructurales: Se prueban todos los caminos posibles que el sistema pueda tener (caja blanca).
- Pruebas de configuración: Se prueba el producto cambiando las configuraciones de este, esto con el objetivo de comprobar el comportamiento del producto frente a este cambio.

## Roles
- Lider de pruebas.
    - Identificar el alcance de las pruebas.
    - Asignar recursos a los proyectos.
    - Definir el perfil de tester que el proyecto necesita.
    - Definir y revisar las estrategias de Testing.
    - Decidir sobre las herramientas a utilizar.
    - Revisar semanalmente el progreso del proyecto.
    - Mitigar los riesgos.
    - Garantizar que los procesos de calidad se siguen y se cumplen.
- Analista de pruebas.
    - Conocer la tecnología del proyecto.
    - Participar en las reuniones de requerimientos.
    - Encargados de crear el documento de análisis de tests.
    - Ver que requisitos se pueden automatizar.
    - Conocer las normas de las estrategias de pruebas.
- Tester.
    - Encargado de escribir y ejecutar las pruebas.
    - Detectar potenciales fallos.
    - Realizar pruebas manuales y automatizadas.
    - Revisar la documentación.
    - Es curioso.
    - Es minucioso en el detalle.
    - Es imaginativo.
    - Es buen comunicador.