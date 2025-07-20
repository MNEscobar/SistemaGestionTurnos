# Abstracción

## Descripción 
La abstracción consiste en identificar y modelar las características esenciales de un objeto, ignorando aquellos detalles que no son relevantes para el contexto del sistema. Es decir, implica representar entidades del mundo real mediante clases que contienen únicamente lo necesario para cumplir un propósito específico dentro del software, dejando de lado la información que no aporta al funcionamiento del sistema que se está desarrollando.
### ¿Por que es importante?
Gracias a la abtraccion se simplifica el sistema mostrando solo lo necesario para cada clase, haciendo el código más facil de leer, mantener y extender. Se mejora la separación de responsabilidades, asignando a cada clase tareas bien definidas. Esto promueve el desarrollo de sistemas más modulares, flexibles y estables.
### Relación con los Principios SOLID
- SRP: La abstracción ayuda a definir clases que tienen una única razón para cambiar, enfocándose solo en una parte del comportamiento del sistema.
- DIP: Este principio se basa en programar interfaces o clases abstractas en lugar de implementaciones concretas. Esto reduce el acoplamiento entre componentes y mejora la flexibilidad del diseño.
### Relación con patrones de diseño
Muchos patrones de diseño se basan en la abstracción para separar responsabilidades y permitir la extensión del sistema sin modificar código existente. Por ejemplo:

- Factory Method o Abstract Factory: abstraen el proceso de creación de objetos.
- Strategy: permite definir una familia de algoritmos intercambiables mediante una interfaz común.
- Observer: abstrae la relación entre un sujeto y sus observadores para permitir una comunicación desacoplada.

---

## Ejemplo en el proyecto

![Imagen](https://drive.google.com/uc?export=view&id=1fbZBMvx-B4QPKf2u4PReQkCcCRTiVHRe)

[Drive](https://drive.google.com/file/d/1fbZBMvx-B4QPKf2u4PReQkCcCRTiVHRe/view?usp=sharing)

El diseño del sistema de turnos aplica el principio de abstracción al modelar entidades y comportamientos relevantes del dominio médico de forma simplificada.

Por ejemplo, la clase Turno representa únicamente los datos necesarios para gestionar un turno: médico, paciente, motivo, estado, y un slot con día y hora.
No incluye detalles clínicos, administrativos ni del contexto externo, lo que permite centrarse en la lógica específica del módulo de turnos.

Además, el sistema define interfaces como notificadorTurno, gestionDeTurno y creadorTurno, que abstraen comportamientos clave del sistema sin acoplarse a una implementación concreta. Esto permite que distintas clases implementen la misma funcionalidad de diferentes maneras, sin afectar al resto del sistema.

### Código de ejemplo

public class Turno {
    private Paciente paciente;
    private Medico medico;
    private Slot slot;
    private String motivo;
    private TurnoEstado estado;
    private boolean notificado;

    public Turno(Paciente paciente, Medico medico, Slot slot, String motivo) {
        this.paciente = paciente;
        this.medico = medico;
        this.slot = slot;
        this.motivo = motivo;
        this.estado = TurnoEstado.PENDIENTE;
        this.notificado = false;
    }

    public Paciente getPaciente() {
        return paciente;
    }

    public Medico getMedico() {
        return medico;
    }

    public Slot getSlot() {
        return slot;
    }

    public String getMotivo() {
        return motivo;
    }

    public TurnoEstado getEstado() {
        return estado;
    }

    public boolean isNotificado() {
        return notificado;
    }

    public void marcarComoNotificado() {
        this.notificado = true;
    }

    public String detalleTurno() {
        return "Turno con Dr. " + medico.getNombre() + " el " + slot.getFechaHora();
    }
}
