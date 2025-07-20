# Encapsulamiento

## Descripción
El encapsulamiento conciste de agrupar los datos (atributos) y los métodos (comportamientos) que operan sobre esos datos dentro de una misma clase, y la ocultación de información gestionando el control de acceso.
Significa que los detalles internos de cómo una clase funciona o cómo almacena sus datos se mantienen ocultos del mundo exterior.

### ¿Por qué es importante?
El encapsulamiento evita el acceso directo y la manipulación de los datos internos de un objeto. Esto garantiza la protección de los datos e integridad de la clase. Al ocultar los detalles de implementación, el resto del sistema que utilizan esta clase no necesitan saber cómo funciona internamente, solo cómo interactuar con su interfaz pública. Si los detalles internos de la clase cambian, las otras partes del sistema no se verán afectadas. Esto reduce la complejidad global y facilita el mantenimiento y la evolución del software.

### Relación con los Principios SOLID
- SRP: Al agrupar los datos y la lógica que operan sobre esos datos en una sola clase, dándole una única razón para cambiar. Los detalles internos se ocultan, reforzando la idea de que la clase solo tiene una responsabilidad bien definida.
- OCP: Una clase debe estar abierta para extensión pero cerrada para modificación. Cuando los detalles internos están encapsulados (cerrados a la modificación externa), puedes extender la funcionalidad de la clase (abierta para extensión) sin tocar su código fuente.
- ISP: El encapsulamiento, al definir interfaces públicas limpias, contribuye a que las interfaces expuestas por una clase solo contienen lo que sus clientes realmente necesitan, sin exponer detalles internos innecesarios.

 ### Relación con patrones de diseño
 El encapsulamiento es un tema recurrente y una base para la mayoría de los patrones de diseño:
- Patrones creacionales (Factory Method, Singleton, Builder): Estos patrones encapsulan la lógica de creación de objetos. **Factory Method**, encapsula la lógica de decidir qué clase concreta crear, liberando al cliente de conocer ese detalle. **Singleton** encapsula la única instancia de una clase y su acceso, controlando estrictamente su creación. **Builder** encapsula el proceso paso a paso de construir objetos complejos, presentando una interfaz simplificada al cliente.
- Patrones Estructurales (Facade, Decorator): El Facade encapsula un subsistema complejo detrás de una interfaz simple, ocultando las interacciones entre múltiples clases. El Decorator encapsula el objeto original que se decora.
- Patrones de Comportamiento (Strategy, State): En el Patrón State encapsula un estado y delega el comportamiento específico a un objeto, ocultando la lógica de transición y los detalles de cada estado. El Patrón Strategy encapsula diferentes algoritmos, permitiendo que un cliente cambie su comportamiento sin conocer los detalles de cada estrategia.

 ---

## Ejemplo en el proyecto

![Imagen](https://drive.google.com/uc?export=view&id=1Uo7BZJ2SxzHQbfhrLXx76ZvDNwXrzNv1)

[Drive](https://drive.google.com/file/d/1Uo7BZJ2SxzHQbfhrLXx76ZvDNwXrzNv1/view?usp=sharing)


En el sistema de gestión de turnos, el fundamento del encapsulamiento se aplica consistentemente para asegurar la integridad de los datos y promover la modularidad del diseño. Cada clase agrupa sus datos con sus comportamientos que los manipulan, manteniendo los detalles internos ocultos del acceso externo directo. Esta práctica asegura que el estado interno de un objeto sea inaccesible, forzando toda interacción a través de una interfaz pública definida.
Cada entidad del sistema, se modela como una unidad autónoma responsable de la gestión de sus propios datos. Los atributos de estas clases son protegidos, y cualquier modificación o consulta de su estado se canaliza mediante métodos públicos. Estos métodos actúan como puertas de control, encapsulando la lógica de negocio, las validaciones y las transiciones de estado, garantizando que el objeto siempre permanezca en un estado válido y consistente.

### Código de ejemplo

```java

public class Paciente {
    private String dni;
    private String nombre;
    private String apellido;
    private Date fechaNacimiento;
    private String email;
    private String obraSocial; 

    public Paciente(String dni, String nombre, String apellido, Date fechaNacimiento, String email, String obraSocial) {
        this.dni = Objects.requireNonNull(dni, "El DNI no puede ser nulo.");
        this.nombre = Objects.requireNonNull(nombre, "El nombre no puede ser nulo.");
        this.apellido = Objects.requireNonNull(apellido, "El apellido no puede ser nulo.");
        this.fechaNacimiento = Objects.requireNonNull(fechaNacimiento, "La fecha de nacimiento no puede ser nula.");
        this.email = Objects.requireNonNull(email, "El email no puede ser nulo.");
        this.obraSocial = Objects.requireNonNull(obraSocial, "La obra social no puede ser nula.");
    }

    public String getDni() {
        return dni;
    }

    public String getNombre() {
        return nombre;
    }

    public String getApellido() {
        return apellido;
    }

    public Date getFechaNacimiento() {
        return fechaNacimiento;
    }

    public String getEmail() {
        return email;
    }

    public String getObraSocial() {
        return obraSocial;
    }

    public void actualizarEmail(String nuevoEmail) {
        if (nuevoEmail != null && !nuevoEmail.trim().isEmpty() && nuevoEmail.contains("@")) {
            this.email = nuevoEmail;
            System.out.println("Email actualizado a: " + this.email);
        } else {
            System.out.println("Error: Email inválido.");
        }
    }

    public void cambiarObraSocial(String nuevaObraSocial) {
        if (nuevaObraSocial != null && !nuevaObraSocial.trim().isEmpty()) {
            this.obraSocial = nuevaObraSocial;
            System.out.println("Obra social actualizada a: " + this.obraSocial);
        } else {
            System.out.println("Error: Obra social inválida.");
        }
    }
}
