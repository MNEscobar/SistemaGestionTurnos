# Principio Abierto/Cerrado (OCP)
En muchos sistemas mal diseñados, cuando es necesario agregar una nueva funcionalidad, se termina modificando directamente el código de clases existentes. Esto puede generar errores inesperados, romper comportamientos previos y volver el sistema difícil de mantener y escalar.

El Principio de Abierto/Cerrado, el segundo principio de SOLID, plantea que una clase debe estar abierta para ser extendida, pero cerrada para ser modificada. Esto significa que deberíamos poder sumar nuevas capacidades o variaciones de comportamiento sin alterar el funcionamiento interno de lo que ya está hecho y probado.

Este principio invita a pensar el diseño orientado a objetos de forma que permita crecimiento sin alterar el código existente. Para eso se suele utilizar abstracción, herencia, interfaces o composición, buscando que el sistema sea adaptable y resistente a cambios.

## Aplicación al sistema de gestión de turnos

En el sistema que estamos desarrollando, hay varias situaciones donde aplicar este principio mejoraría la organización y estabilidad del código. Una de ellas es en la forma en que el administrador visualiza las estadísticas del sistema.

Actualmente, la clase Administrador contiene un método llamado verEstadísticas(). Si quisiéramos mostrar nuevas estadísticas (por ejemplo, cantidad de turnos cancelados, turnos por especialidad médica o estadísticas por paciente), tendríamos que entrar al método y modificarlo directamente para agregar nuevas lógicas. Esto es una violación del principio, porque cada nuevo requerimiento obliga a intervenir en código que ya funciona.

La forma correcta de aplicar OCP en este caso sería diseñar el sistema para que las distintas formas de generar estadísticas sean independientes entre sí y puedan ser agregadas como nuevas "variantes" sin modificar el comportamiento central de la clase Administradora. Es decir, en lugar de tener un único método con muchos casos posibles dentro, podríamos delegar la lógica en componentes o estructuras separadas, cada una con una única función. Así, si más adelante se quiere incorporar una nueva métrica, simplemente se añade una nueva funcionalidad sin tocar nada de lo ya hecho.

Otro caso donde aplicar este principio sería útil es en la forma en que se gestionan las notificaciones desde la clase Turno. Actualmente, existe un método enviarCorreo, que podría complicarse si se agregan distintos tipos de correos (recordatorio, confirmación, cancelación, encuesta, etc.). Si cada tipo de correo requiere modificar el método, se vuelve difícil de mantener.

Aplicando OCP, podríamos pensar cada tipo de notificación como una responsabilidad separada. De esa manera, cuando se quiera agregar un nuevo tipo de aviso, se podrá incorporar como una extensión del sistema sin necesidad de modificar el método original.

En ambos casos, el principio nos ayuda a aislar los cambios y evitar afectar lo que ya está funcionando, lo cual es clave para el crecimiento del sistema a largo plazo.

## Ejemplo del mundo real
Imaginemos un restaurante que tiene un menú impreso. Cada vez que quiere agregar un nuevo plato, tiene que volver a imprimir toda la carta. Esto genera un gasto innecesario y riesgo de errores. En cambio, si el menú está pensado de forma modular, con secciones editables o digitales, el restaurante puede agregar opciones nuevas sin modificar lo que ya funciona. Este enfoque, que separa lo existente de lo nuevo sin afectar lo anterior, es exactamente lo que busca el principio de abierto/cerrado.


## Grafico del Principio OCP aplicado al sistema 

![Imagen](https://drive.google.com/uc?export=view&id=1pNRaGwQKxnDWHSFyed6pwB49bHRAsxIQ)

[Drive](https://drive.google.com/file/d/1pNRaGwQKxnDWHSFyed6pwB49bHRAsxIQ/view?usp=sharing)
