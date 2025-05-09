# Principio de Sustitución de Liskov (LSP)

Uno de los problemas más comunes en sistemas mal diseñados ocurre cuando se intenta reutilizar una clase hija en lugar de su clase padre y el comportamiento no es el esperado. Esto genera errores silenciosos, incoherencias y pérdida de confianza en la jerarquía del sistema.

El Principio de Sustitución de Liskov, tercer principio de SOLID, establece que los objetos de una clase derivada deben poder sustituir a los objetos de su clase base sin alterar el comportamiento del programa. Es decir, si una clase Hija hereda de una clase Padre, debería poder usarse en cualquier lugar donde se espere un objeto del tipo Padre sin que eso genere errores o comportamientos incorrectos.

Este principio pone el foco en preservar el contrato de la clase base: si una subclase rompe ese contrato o modifica cómo se espera que funcione la superclase, se está violando el LSP, y el sistema se vuelve frágil, inconsistente y difícil de mantener.

## Aplicación al sistema de gestión de turnos

En el sistema, las clases Paciente, Administrador y Médico heredan de la clase base Usuario. Esto significa que cualquier instancia de esas clases debería poder ser utilizada como un Usuario sin afectar el comportamiento esperado del sistema.

La clase usaurio llama a métodos como registrarse(), verPerfil() o iniciarSesion(), entonces cualquier objeto Paciente, Administrador o Médico también debería poder realizar esas acciones sin generar errores ni comportamientos inesperados.

Por el contrario, si alguna de estas subclases anula los métodos heredados de Usuario de manera que cambian su funcionamiento esencial (por ejemplo, un Médico que no puede iniciar sesión, o un Administrador cuyo método verPerfil() arroja error), entonces el sistema estaría violando el principio de Liskov, ya que no se podría sustituir a un Usuario por una subclase sin consecuencias.

Otro ejemplo posible: imaginá que en algún punto del sistema se quiere tratar a todos los usuarios como una lista común para mostrar perfiles. Si una subclase no respeta la estructura esperada o no implementa adecuadamente lo que el sistema necesita, esa generalización se rompe y se generan fallos o excepciones.

Aplicar correctamente este principio significa asegurarse de que todas las subclases mantengan la coherencia funcional de la clase base, evitando alterar comportamientos que deberían ser comunes. Si una subclase necesita modificar demasiado el funcionamiento de la clase padre, probablemente esté mal ubicada en la jerarquía o necesite una abstracción diferente.

## Ejemplo del mundo real

Pensemos en un enchufe estándar. Si fabricamos electrodomésticos que se enchufan a una toma común, esperamos que cualquiera de esos dispositivos funcione al conectarse. Si un nuevo electrodoméstico necesita un tipo de conexión diferente o hace saltar la llave de luz, entonces no respeta el contrato de uso del enchufe común, y se vuelve incompatible. Este ejemplo ilustra cómo romper el principio de Liskov genera fallos incluso cuando “heredamos” del mismo estándar.
