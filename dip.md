# Principio de Inversión de Dependencias (DIP)

El Principio de Inversión de Dependencias establece que los módulos de alto nivel no deben depender de los módulos de bajo nivel, sino que ambos deben depender de abstracciones. Además, las abstracciones no deben depender de los detalles, sino que los detalles deben depender de las abstracciones.

Esto significa que el diseño del sistema debe orientarse a lo general y no a lo específico. Los componentes más importantes del sistema (como las reglas de negocio o la lógica central) no deberían estar acoplados directamente a implementaciones concretas (como métodos de almacenamiento, validaciones o notificaciones). En cambio, deberían trabajar sobre estructuras más generales (interfaces, contratos, abstracciones) que luego pueden ser implementadas o modificadas sin afectar el funcionamiento global.

En muchos sistemas mal diseñados, los módulos principales dependen directamente de clases concretas que realizan tareas específicas. Por ejemplo, una clase de gestión de turnos puede depender directamente de una clase que envía correos, almacena en base de datos o calcula estadísticas. Esto genera un acoplamiento rígido, haciendo que cada cambio en una funcionalidad secundaria obligue a modificar la clase principal, dificultando la escalabilidad, el mantenimiento y las pruebas.

El DIP soluciona esto proponiendo que los detalles (como el envío de correos o el registro en la base de datos) estén aislados detrás de una capa de abstracción, permitiendo que la lógica principal no se vea afectada por los cambios en esas implementaciones.

## Aplicación al sistema de gestión de turnos

En el sistema de gestión de turnos, el DIP se puede aplicar al organizar cómo las clases se relacionan con funcionalidades secundarias como el envío de correos, la visualización de estadísticas o la persistencia de datos.

Por ejemplo, actualmente el método enviarCorreo() está implementado directamente en la clase Turno, lo que significa que esa clase conoce y depende del detalle técnico de cómo se envían los correos. Si en el futuro se decide cambiar el servicio de correo (por ejemplo, de SMTP a una API externa), habría que modificar directamente la clase Turno, afectando potencialmente su funcionamiento.

Una mejor forma de aplicar DIP sería definir una abstracción general, como una interfaz o contrato conceptual del tipo Notificador, que tenga un método genérico como notificarTurnoConfirmado(). Luego, esa interfaz puede ser implementada por una clase NotificadorPorCorreo, sin que Turno dependa directamente de cómo se envía el correo. De esta forma, si se quiere cambiar el medio de notificación (correo, mensaje de texto, etc.), no se toca la lógica de Turno, sino solo la implementación concreta del notificador.

Lo mismo puede aplicarse a la generación de estadísticas en la clase Administradora, o a la forma en que los usuarios se autentican. Al depender de abstracciones, el sistema es más modular, mantenible y preparado para el cambio.

## Ejemplo del mundo real

Imaginá una empresa que organiza eventos y tiene un sistema para contratar servicios como catering, música o iluminación. La persona encargada de coordinar eventos no necesita saber si el catering es provisto por un restaurante, un chef independiente o un food truck. Solo necesita que el servicio contratado cumpla con ciertas condiciones: entregar comida a cierta hora, para cierta cantidad de personas.

En este caso, el coordinador depende de una abstracción de “servicio de catering”, no del proveedor específico. Esto le permite cambiar fácilmente de proveedor sin tener que replantear toda la organización del evento.


## Diagrama de el Principio DIP aplicado al Sistema

![Imagen](https://drive.google.com/uc?export=view&id=17-lG_x91jSKeHymx6_40aW192Vd72hfc)

[Drive](https://drive.google.com/file/d/17-lG_x91jSKeHymx6_40aW192Vd72hfc/view?usp=sharing)
