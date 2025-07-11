# 7. Vista de Despliegue

## Descripción General

La Vista de Despliegue describe la infraestructura técnica necesaria para ejecutar los sistemas de la Estrella de la Muerte, incluyendo los componentes de hardware, distribución geográfica, topología de red y entornos de cómputo. Esta sección también muestra cómo los componentes de software se asignan a los elementos de infraestructura.

## Entornos

La Estrella de la Muerte opera en varios entornos distintos para garantizar eficiencia, seguridad y redundancia:
- **Desarrollo**: Utilizado por ingenieros para probar y actualizar sistemas antes del despliegue.
- **Pruebas**: Entorno aislado para pruebas rigurosas sin afectar los sistemas operativos.
- **Producción**: El entorno operativo principal donde todos los sistemas están activos y listos para el mando imperial.
> **Nota:**  
> Los entornos de Desarrollo, Pruebas y Producción comparten el mismo centro de datos físico. La separación se garantiza de forma lógica, no mediante instalaciones de hardware independientes.


## Componentes Clave de Infraestructura

1. **Núcleo del Reactor Central**: Proporciona energía para todos los sistemas, ubicado en el centro de la Estrella de la Muerte.
2. **Centros de Datos**: Distribuidos en múltiples sectores para gestionar datos y comunicaciones.
3. **Matriz de Comunicaciones**: Ubicada en el exterior para transmisiones seguras con el Comando Imperial.
4. **Nodos de Control de Seguridad**: Gestionan el acceso y monitorean la actividad en toda la estación.

## Topología de Red

La red interna de la Estrella de la Muerte está organizada para garantizar un flujo de datos seguro y eficiente:
- **Red de Comando**: Conecta el comando central con sistemas críticos como el superláser y el núcleo del reactor.
- **Red de Seguridad**: Gestiona la vigilancia y los nodos de control de seguridad.
- **Red de Comunicaciones**: Dedicada a transmisiones externas e informes de estado internos.

### Diagrama


```mermaid
graph TD
    %% Entornos principales
    subgraph Entorno_Produccion["Entorno de Producción"]
        subgraph Estrella_Muerte["Sistemas Principales de la Estrella de la Muerte"]
            Reactor_Central["Núcleo del Reactor Central<br><i>Energía para todos los sistemas</i>"]
            Centros_Datos["Centros de Datos<br><i>Distribuidos por sectores</i>"]
            Matrices_Comunicacion["Matrices de Comunicación<br><i>Transmisión externa</i>"]
            Nodos_Seguridad["Nodos de Control de Seguridad<br><i>Acceso y monitorización</i>"]
        end
    end

    subgraph Entorno_Pruebas["Entorno de Pruebas"]
        Sistemas_Pruebas["Sistemas de Pruebas Aislados"]
    end

    subgraph Entorno_Desarrollo["Entorno de Desarrollo"]
        Sistemas_Desarrollo["Sistemas de Desarrollo"]
    end

    %% Topología de red
    Reactor_Central -->|Red de Comando| Centros_Datos
    Centros_Datos -->|Red de Comando| Matrices_Comunicacion
    Centros_Datos -->|Red de Seguridad| Nodos_Seguridad
    Matrices_Comunicacion -->|Red de Comunicaciones| Comando_Imperial["Comando Imperial<br><i>Sede externa</i>"]

    %% Relación entre entornos
    Sistemas_Desarrollo -- "Pipelines de Desarrollo" --> Centros_Datos
    Sistemas_Pruebas -- "Pipelines de Pruebas" --> Centros_Datos


```

## Motivación

Esta estructura de despliegue respalda el alto rendimiento, la seguridad y la tolerancia a fallos, esenciales para la estabilidad operativa de la Estrella de la Muerte. Al separar redes y definir entornos, la arquitectura asegura que cada sistema pueda funcionar de manera independiente y mantener su resiliencia.
