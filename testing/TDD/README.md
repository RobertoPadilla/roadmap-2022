# Test Driven Development

## Flujo normal
1. Levantamiento de requerimientos
2. Diseño del software
3. Desarrollo de software
4. Pruebas
    - Ciclo infinito entre los puntos 3 y 4
5. Salida a producción
    - Falla en producción.
    - Inconvenientes que hay que resolver.

## Flujo del desarrollo con TDD
1. Levantamiento de requerimientos
2. Diseño del software
3. Desarrollo de pruebas
4. Desarrollo de software
    - Ciclo finito entre los puntos 3 y 4
    - Mejora continua y refactorización del código
5. Salida a producción
    - Felicidad del cliente, tester, desarrollador, etc.

## Ventajas
- Mejora contínua de tu código sin tener que preocuparte de dañar algo (Refacturación).
- Tener siepre al día la documentación del código (viendolo desde el punto de vista de lectura de código, no desde la documentación formal).
    - En gran mayoría de los casos, ver los test nos permiten entender el objetivo de nuestro código.
- Reduce el tiempo de salida a producción. (No el tiempo de desarrollo).
- Tests automatizados del lado del código.
    - No debugging. Evita estar revisando manualmente el código intentando encontrar el origen del problema, ya que los test fácilitan encontrarlo.
- Nos obliga a seguir las especificaciones de **Clean Code**.

## Tipos de testing

### The black-box testing o functional testing
Una vez construida la aplicación, esta se le enseña a un tester (no hay necesidad de que tenga conocimientos técnicos ni del modelo de negocio) y este hace pruebas sobre la interfaz gráfica. Cualquier error debemos anotarlo para arreglarlo después.

### The white-box testing o structural testing
Se necesita personal capacitado para hacer este tipo de testing, ya que debe tener conocimiento de desarrollador para realizar las pruebas con código.

## Ciclo de vida de TDD
1. Creación del test.
2. Esperar a que fallen los test (estado rojo).
3. Escribir un código que cumpla lo básico.
4. Esperar a que el test no falle (estado verde).
5. Refactorizar el código, es decir, mejorarlo (es necesario para el cumplimiento del ciclo de vida; estado refactorizar).

## Ciclo RGR
- R (RED): Las pruebas deben fallar.
- G (GREEN): Las pruebas pasan.
- R (REFACTOR): Mejorar el código sin hacer que las pruebas fallen.