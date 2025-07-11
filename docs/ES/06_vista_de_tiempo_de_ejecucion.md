# 6. Vista de Tiempo de Ejecución

## Descripción General

La Vista de Tiempo de Ejecución describe el comportamiento dinámico y las interacciones de los bloques de construcción de la Estrella de la Muerte durante escenarios clave. Esta vista muestra cómo los componentes trabajan juntos para manejar casos de uso importantes, procesos operativos y gestión de errores.

## Escenarios Clave

1. **Secuencia de Destrucción Planetaria**
   - **Desencadenante**: Orden del Comando Imperial.
   - **Secuencia**: El sistema de Comando y Control activa el Sistema de Superláser. El Núcleo del Reactor canaliza energía al Amplificador de Energía, lo que permite al superláser apuntar y destruir el planeta designado.
   - **Gestión de Errores**: Si la salida de energía supera los límites seguros, el Sistema de Enfriamiento regula el flujo de energía para evitar el sobrecalentamiento.
   - **Diagrama de sequencia**:
```mermaid
sequenceDiagram
    participant Comando_Imperial as Mando Imperial
    participant Comando_Control as Comando y Control
    participant Reactor as Núcleo del Reactor
    participant Superlaser as Sistema de Superláser
    participant Enfriamiento as Sistema de Enfriamiento

    Comando_Imperial ->> Comando_Control: Orden de destrucción planetaria
    Comando_Control ->> Superlaser: Activar sistema de arma
    Comando_Control ->> Reactor: Solicitar energía máxima
    Reactor ->> Superlaser: Canalizar energía
    Reactor -->> Enfriamiento: Monitorizar niveles de energía
    Enfriamiento -->> Reactor: Regular energía si hay sobrecalentamiento
    alt Sobrecalentamiento detectado
        Enfriamiento ->> Comando_Control: Notificar riesgo de sobrecalentamiento
        Comando_Control ->> Reactor: Reducir salida de energía
    end
    Superlaser ->> Planeta: Destruir planeta objetivo

```

2. **Detección y Respuesta ante Intrusos**
   - **Desencadenante**: Detección de presencia no autorizada a través de Matrices de Sensores.
   - **Secuencia**: El sistema alerta a Comando y Control, que envía tropas de asalto a la ubicación del intruso.
   - **Gestión de Errores**: En caso de fallo del sistema, se activa una alarma y se despliegan unidades de respaldo manualmente.
   - **Diagrama de sequencia**:
```mermaid
sequenceDiagram
    participant Matrices_Sensores as Matrices de Sensores
    participant Comando_Control as Comando y Control
    participant Tropas_Asalto as Tropas de Asalto
    participant Sistema_Alarmas as Sistema de Alarmas

    Matrices_Sensores ->> Comando_Control: Intrusión detectada
    Comando_Control ->> Tropas_Asalto: Desplegar escuadra al objetivo
    alt Falla del sistema
        Matrices_Sensores ->> Sistema_Alarmas: Activar alarma
        Sistema_Alarmas ->> Comando_Control: Notificar necesidad de respuesta manual
        Comando_Control ->> Tropas_Asalto: Desplegar unidades de respaldo
    end
```

3. **Activación del Hiperimpulsor y Navegación**
   - **Desencadenante**: Orden de Control de Navegación para reubicar la Estrella de la Muerte.
   - **Secuencia**: El Núcleo del Reactor redirige energía al Hiperimpulsor, mientras que los sistemas de Navegación coordinan con Comando y Control para garantizar un viaje seguro a través del hiperespacio.
   - **Gestión de Errores**: Si la navegación falla, la energía se desvía de regreso a otros sistemas, y el Comando inicia protocolos de navegación de respaldo.
   - **Diagrama de sequencia**:
```mermaid
sequenceDiagram
    participant Control_Navegacion as Control de Navegación
    participant Comando_Control as Comando y Control
    participant Reactor as Núcleo del Reactor
    participant Hiperimpulsor as Sistema de Hiperimpulsor

    Control_Navegacion ->> Comando_Control: Solicitar activación del hiperimpulsor
    Comando_Control ->> Reactor: Redirigir energía al hiperimpulsor
    Reactor ->> Hiperimpulsor: Suministrar energía
    Control_Navegacion ->> Hiperimpulsor: Calcular trayectoria en el hiperespacio
    alt Falla de navegación
        Hiperimpulsor ->> Control_Navegacion: Error en trayectoria detectado
        Control_Navegacion ->> Comando_Control: Notificar fallo de navegación
        Comando_Control ->> Reactor: Desviar energía de regreso a sistemas principales
        Comando_Control ->> Control_Navegacion: Iniciar protocolos de navegación de respaldo
    end
```

## Motivación

Esta vista es esencial para comprender las interacciones dinámicas dentro de la Estrella de la Muerte, especialmente durante operaciones críticas. Al documentar estos escenarios, garantizamos una ejecución fluida y una rápida solución de problemas durante procesos complejos.
