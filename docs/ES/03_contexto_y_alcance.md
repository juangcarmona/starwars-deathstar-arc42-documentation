# 3. Contexto y Alcance

## Descripción General

Esta sección define los límites del sistema de la Estrella de la Muerte, identificando sus socios de comunicación externos e interfaces. Distingue entre el contexto de negocio (interacciones específicas del dominio) y el contexto técnico (protocolos de comunicación, canales, hardware).

## Contexto de Negocio

La Estrella de la Muerte interactúa con múltiples sistemas y entidades externas, cada una cumpliendo un rol único. Estas incluyen:
- **Comando Imperial**: Proporciona objetivos de misión, decisiones tácticas y protocolos de seguridad.
- **Flota y Tropas Terrestres**: Coordinación para soporte operativo, logística y despliegue de recursos.
- **Gobernadores Planetarios**: Interfaces para autoridad jurisdiccional, vigilancia y control.

### Diagrama de Contexto de Negocio

```mermaid
%% Death Star Business Context Diagram
graph TD
    subgraph Galactic_Empire ["Imperio Galáctico"]
        deathstar["Estrella_de_la_Muerte<br><i>Arma definitiva y estación espacial móvil</i>"]
    end

    emperor["Emperador Palpatine<br><i>Líder supremo del Imperio Galáctico</i>"]
    imperial_command["Mando_Imperial<br><i>Objetivos y decisiones estratégicas</i>"]
    imperial_fleet["Flota_Imperial<br><i>Destructores Estelares y naves de apoyo</i>"]
    ground_troops["IFuerzas Terrestres Imperiales<br><i>Soldados de asalto y unidades militares</i>"]
    planetary_gov["Gobernadores Planetarios<br><i>Administradores regionales</i>"]
    rebel_alliance["Alianza Rebelde<br><i>Movimiento de Resistencia</i>"]
    trade_federation["Comercio Federación<br><i>Entidades económicas controladas por el Imperio</i>"]

    emperor -->|Órdenes| deathstar
    imperial_command -->|Directivas estratégicas<br><i>Canales seguros</i>| deathstar
    deathstar -->|Coordina operaciones<br><i>Red táctica</i>| imperial_fleet
    deathstar -->|Órdenes de despliegue<br><i>Canales militares</i> | ground_troops
    deathstar -->|Aplica el cumplimiento<br><i>Interfaz de administración</i>| planetary_gov
    planetary_gov -->|Informes de inteligencia<br><i>Datos de vigilancia</i>| deathstar
    deathstar -->|Suprime<br><i>Acción militar</i>| rebel_alliance
    deathstar -->|Controla<br><i>Directivas económicas</i>| trade_federation

```

## Contexto Técnico

El contexto técnico se centra en las interfaces, protocolos y canales de comunicación necesarios para que la Estrella de la Muerte interactúe con su entorno. Esto incluye:
- **Transmisión de Datos**: Canales seguros para el mando y control desde el Comando Imperial.
- **Sistemas de Armas**: Interfaces para control de objetivos, distribución de energía y control de disparo.
- **Sistemas de Sensores**: Monitoreo continuo del espacio circundante y cuerpos planetarios.

### Diagrama de Contexto Técnico

```mermaid
%% Diagrama de Contexto Técnico de la Estrella de la Muerte – Ordenado según PlantUML LAYOUT_TOP_DOWN
graph TD
    %% Capa superior: actor externo
    imperial_command["Comando Imperial<br><i>Comando estratégico que proporciona objetivos de misión</i>"]

    %% Segunda capa: punto de entrada de comunicaciones
    comm_system["Comunicaciones<br><i>Canales cifrados</i><br>Comunicación segura con las fuerzas imperiales"]

    imperial_command -->|Órdenes estratégicas<br><i>Comunicaciones cifradas por el hiperespacio</i>| comm_system

    %% Límite del sistema de la Estrella de la Muerte
    subgraph Death_Star_System["Sistema de la Estrella de la Muerte"]
        command_center["Centro de Mando<br><i>Sistema Operativo Imperial</i><br>Sistema central de mando y control"]
        weapon_control["Control del Superláser<br><i>Sistema de control en tiempo real</i><br>Apuntado y disparo del arma principal"]
        shield_generator["Generador de Escudos<br><i>Sistemas electromagnéticos</i><br>Escudos planetarios"]
        sensor_array["Matriz de Sensores<br><i>Sistemas de detección avanzada</i><br>Escaneo espacial y planetario"]
        power_core["Reactor Principal<br><i>Reactor de hipermateria</i><br>Generación de energía"]
        life_support["Soporte Vital<br><i>Control ambiental</i><br>Atmósfera y gravedad"]
        docking_bays["Bays de Acoplamiento<br><i>Gestión de naves</i><br>Operaciones de cazas y transportes"]
    end

    comm_system -->|Datos de misión<br><i>Canales internos seguros</i>| command_center

    command_center -->|Órdenes de disparo<br><i>Bus de control de alta prioridad</i>| weapon_control
    command_center -->|Peticiones de escaneo<br><i>Protocolo de control de sensores</i>| sensor_array
    command_center -->|Órdenes de escudo<br><i>Protocolo de control de defensa</i>| shield_generator

    power_core -->|Alimentación de energía masiva<br><i>Conductos de energía primaria</i>| weapon_control
    power_core -->|Energía para escudos<br><i>Red de energía secundaria</i>| shield_generator
    power_core -->|Energía para sensores<br><i>Líneas de alimentación auxiliares</i>| sensor_array
    power_core -->|Energía ambiental<br><i>Red de soporte vital</i>| life_support

    %% Sistemas externos en la capa inferior
    imperial_network["Red Imperial<br><i>Infraestructura galáctica de comunicaciones</i>"]
    star_destroyers["Flota de Destructores Estelares<br><i>Naves de apoyo táctico</i>"]
    tie_fighters["Escuadrón de Cazas TIE<br><i>Cazas estelares</i>"]
    planetary_sensors["Redes de Sensores Planetarios<br><i>Detección desde superficie</i>"]
    hyperspace_beacons["Red de Balizas Hiperespaciales<br><i>Infraestructura de navegación</i>"]

    sensor_array -->|Datos de inteligencia<br><i>Transmisión por ráfagas</i>| imperial_network
    comm_system -->|Coordinación de flota<br><i>Protocolos de comunicaciones militares</i>| star_destroyers
    comm_system -->|Sincronización de navegación<br><i>Posicionamiento hiperespacial</i>| hyperspace_beacons
    docking_bays -->|Despliegue de cazas<br><i>Sistemas de control de lanzamiento</i>| tie_fighters
    sensor_array -->|Fusión de sensores<br><i>Protocolos de correlación de datos</i>| planetary_sensors
```


## Motivación

Comprender el contexto de negocio y técnico asegura que todas las dependencias externas estén gestionadas y que las interacciones de la Estrella de la Muerte con otros sistemas sean fluidas. La documentación adecuada de estas interfaces es crítica para evitar malentendidos o fallos en situaciones de alta importancia.
