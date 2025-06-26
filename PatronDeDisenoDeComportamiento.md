# Patrón de diseño de comportamiento

## ¿Qué son los patrones de diseño de comportamiento?
Los patrones de diseño de comportamiento se centran en cómo interactúan los objetos y cómo se asignan responsabilidades entre ellos para llevar a cabo operaciones y flujos de control dentro de un sistema. Su objetivo es mejorar la comunicación, la flexibilidad y la extensibilidad del comportamiento, desacoplando quién invoca una acción de quién la implementa.

### Ejemplo de tipos de patrones de comportamiento
- Strategy
- Observer
- Command
- State
- Template Method

---

## Relación con los principios SOLID
Los patrones de comportamiento refuerzan varios principios SOLID al nivel de colaboración entre objetos:

---

### Principio de Responsabilidad Única (SRP)
Cada patrón aísla una responsabilidad concreta dentro del flujo de ejecución; en el patrón *Command*, por ejemplo, cada objeto de comando se encarga exclusivamente de representar y ejecutar una petición determinada.

---

### Principio de Abierto/Cerrado (OCP)
Permiten extender el comportamiento sin modificar el código existente; al usar *Strategy*, se pueden añadir nuevas estrategias de notificación sin tocar la clase cliente que las invoca.

---

### Principio de Sustitución de Liskov (LSP)
Todas las implementaciones de *Observer* o *State* respetan el contrato definido por su interfaz, de modo que pueden sustituirse unas por otras sin romper la lógica de notificación o de transición de estados.

---

### Principio de Segregación de Interfaces (ISP)
Exponen interfaces muy específicas para cada rol de colaboración; un cliente de *Observer* depende únicamente de `update()`, sin verse cargado de métodos que no necesita.

---

### Principio de Inversión de Dependencias (DIP)
el sistema interactúa siempre con abstracciones de comportamiento; por ejemplo, el contexto de *State* invoca solo métodos de la interfaz de estado, sin conocer ni depender de las clases concretas que los implementan.

---

## Propósito y Tipo de patrón
Para gestionar de forma dinámica el comportamiento de un `Turno` según su estado (Pendiente, Confirmado, Cancelado) y delegar en cada caso la lógica específica de acciones como notificar, habilitar o bloquear operaciones, se elige aplicar el patrón State, un patrón de comportamiento que encapsula cada estado en una clase concreta y permite cambiar el comportamiento de `Turno` en tiempo de ejecución sin condicionales dispersos.

---

## Motivación
En el diseño actual, el objeto `Turno` mantiene un atributo estado de tipo enum (PENDIENTE, CONFIRMADO, CANCELADO) y, cada vez que debe ejecutar una operación (por ejemplo, cancelar o notificar), recurre a múltiples sentencias para decidir qué hacer según el valor de ese enum. Este enfoque dispersa la lógica de comportamiento por toda la clase `Turno`, hace crecer el número de condicionales a medida que introducimos nuevas acciones o estados, y dificulta la prueba y el mantenimiento del código.
Para solucionar esto, introducimos el patrón ***State***, que extrae cada comportamiento asociado a un estado en su propia clase.

### Funcion de las nuevas clases
`EstadoTurno` (interfaz) define las operaciones comunes, por ejemplo `cancelar()`, `confirmar()`, `notificar()`.

`PendienteState`, `ConfirmadoState` y `CanceladoState` (clases concretas) implementan estas operaciones de manera específica: `PendienteState.cancelar()` marca el turno como cancelado y programa la anulaciónde la notificación, mientras que en `ConfirmadoState.notificar()` envía el recordatorio 24 hs antes.

La clase `Turno` pasa a tener solo un atributo `estado: EstadoTurno` y cada llamada a `turno.cancelar()` o `turno.notificar()` se delega directamente a `estado.cancelar()` o `estado.notificar()` sin ningún condicional. Además, `Turno` expone un método `setEstado(EstadoTurno nuevoEstado)` que permite cambiar dinámicamente el comportamiento al transicionar de un estado a otro. Con este diseño se busca eliminar la proliferación de condicionales y se agrupa la lógica de cada estado en su propia clase.

---

## Estructura de Clases

![Imagen](https://drive.google.com/uc?export=view&id=1XkarsGBcwnosgVLXuCBL_cnTD01w5mdF)

[Drive](https://drive.google.com/file/d/1XkarsGBcwnosgVLXuCBL_cnTD01w5mdF/view?usp=sharing)
