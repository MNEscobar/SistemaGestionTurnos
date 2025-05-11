# Principio de Segregación de Interfaces (ISP)

El Principio de Segregación de Interfaces (ISP) establece que una clase no debe estar forzada a implementar métodos que no necesita o no utiliza. Es decir, es preferible tener interfaces específicas y pequeñas, orientadas a necesidades particulares, antes que una sola interfaz genérica que lo abarque todo.

Este principio se relaciona con la idea de que cada clase debe tener solo las dependencias que realmente le interesan. Así se promueve un diseño modular, más fácil de entender, extender y mantener.

Uno de los errores frecuentes en sistemas mal diseñados es crear interfaces o estructuras con demasiadas responsabilidades, obligando a las clases que las implementan a depender de métodos que no usan o que no les corresponden. Esto genera confusión, acoplamiento innecesario y obliga a los desarrolladores a mantener código irrelevante para el rol de esa clase.

## Aplicación al sistema de gestión de turnos

En el diseño de este sistema, este principio se encuentra aplicado, ya que se construyó una clase base llamada Usuario, que contiene únicamente métodos y atributos comunes a todos los tipos de usuarios, como registrarse(), iniciarSesion() y verPerfil(). Estos métodos son necesarios tanto para Paciente, Médico como para Administradora, por lo tanto tiene sentido que estén en la superclase.

Luego, cada tipo de usuario hereda de Usuario y define sus propios métodos específicos:

- Paciente tiene métodos como sacarTurno() y cancelarTurno().
- Médico puede verHistorial() o agregarDiagnóstico().
- Administradora puede gestionarUsuarios() y asignarTurnos().

Esto significa que cada clase trabaja únicamente con los métodos que necesita, sin estar obligada a tener funcionalidades que no le corresponden. De esta forma, el sistema se mantiene limpio, claro y fácil de escalar, cumpliendo con el principio de segregación de interfaces.

Es importante aclarar que si en el futuro la clase Usuario comenzara a acumular responsabilidades que solo competen a ciertos roles (como estadísticas, asignación de turnos o ver historial médico), se correría el riesgo de violar este principio, ya que Paciente o Médico heredarían métodos que no usan. Por eso, mantener esta separación clara es clave para preservar el buen diseño a lo largo del tiempo.

## Ejemplo del mundo real

Un control remoto diseñado para múltiples dispositivos (TV, DVD, aire acondicionado) puede terminar teniendo botones que no usamos nunca. En cambio, un control diseñado específicamente para la TV, con los botones justos, es más claro, cómodo y fácil de usar. El ISP busca exactamente eso: que cada “control” (clase) tenga solo los comandos que necesita.


## Diagrama de el principio ISP aplicado al Sistema

![Imagen](https://drive.google.com/uc?export=view&id=1DzA_VvA1cxzc-6ROvK-ma7oS61ER7Ut_)

[Drive](https://drive.google.com/file/d/1DzA_VvA1cxzc-6ROvK-ma7oS61ER7Ut_/view?usp=sharing)
