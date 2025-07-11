# 9. Decisiones Arquitectónicas

## Descripción General

Esta sección documenta las decisiones arquitectónicas críticas que han dado forma al diseño y funcionalidad de la Estrella de la Muerte. Cada decisión incluye su contexto, las opciones consideradas, la elección final y la justificación detrás de ella. Estas decisiones son significativas por su impacto en la funcionalidad, el rendimiento o la seguridad general.

## Principales Decisiones Arquitectónicas

1. **Reactor Centralizado de Energía**: 
   - **Contexto**: La Estrella de la Muerte requiere una gran cantidad de energía para alimentar su superláser.
   - **Opciones**: Varios reactores pequeños frente a un reactor centralizado único.
   - **Decisión**: Utilizar un **único reactor central** para optimizar la gestión y amplificación de energía para el superláser.
   - **Razonamiento**: Un solo reactor permite un control eficiente de la energía y simplifica la integración de sistemas. Sin embargo, **introduce un único punto crítico de fallo**: si el reactor es comprometido, toda la estación queda inoperativa.

> ⚠️ Este riesgo se analiza explícitamente en la Sección 11: [Riesgos y Deuda Técnica](./11_riesgos_y_deuda_tecnica.md).

2. **Diseño Modular para Sistemas de Armamento y Soporte Vital**:
   - **Contexto**: La necesidad de aislar sistemas de alto riesgo, como el armamento, y sistemas críticos, como el soporte vital.
   - **Opciones**: Diseño totalmente integrado versus separación modular de sistemas.
   - **Decisión**: Adoptar un diseño modular para garantizar que una falla en un sistema (por ejemplo, el armamento) no comprometa otras áreas críticas.
   - **Razonamiento**: Esta decisión mejora la tolerancia a fallos y facilita actualizaciones y mantenimiento.

3. **Protocolo de Comunicaciones Seguras**:
   - **Contexto**: Comunicación a través de grandes distancias entre la Estrella de la Muerte y el Comando Imperial.
   - **Opciones**: Protocolos estándar versus un protocolo propietario y encriptado.
   - **Decisión**: Implementar un protocolo propietario de alta seguridad para todas las transmisiones.
   - **Razonamiento**: Garantiza comunicaciones seguras, protegiendo información sensible de la posible interceptación Rebelde.

4. **Sistema Automático de Detección de Intrusos**:
   - **Contexto**: Alto riesgo de infiltraciones rebeldes o sabotaje.
   - **Opciones**: Monitoreo de seguridad manual versus detección automática de intrusiones.
   - **Decisión**: Utilizar un sistema automatizado para detectar y responder a intentos de acceso no autorizado.
   - **Razonamiento**: La automatización permite tiempos de respuesta más rápidos, reduciendo el riesgo de amenazas internas y externas.





### Tabla Resumen de Decisiones
| ID | Título de la Decisión                         | Estado | Nivel de Impacto | Sistemas Afectados                       |
| -- | --------------------------------------------- | ------ | ---------------- | ---------------------------------------- |
| 1  | Reactor Centralizado                          | Activa | Crítico          | Núcleo del Reactor                       |
| 2  | Diseño Modular para Armas y Soporte Vital     | Activa | Alto             | Sistemas de Armas, Soporte Vital         |
| 3  | Protocolo de Comunicaciones Seguras           | Activa | Alto             | Matriz de Comunicaciones                 |
| 4  | Sistema Automatizado de Detección de Intrusos | Activa | Medio            | Sistemas de Monitoreo, Comando y Control |



## Motivación

Documentar estas decisiones arquitectónicas proporciona una comprensión clara de las elecciones que guían la estructura y funcionalidad de la Estrella de la Muerte. Esta documentación garantiza la continuidad en el diseño e informa el desarrollo o las modificaciones futuras para mantener la alineación con los objetivos iniciales.

## NOTA SOBRE ADR:

Las decisiones documentadas aquí siguen el formato **Architectural Decision Record (ADR)**, una práctica formalizada dentro de la doctrina técnica del Imperio Galáctico.

Históricamente, los ADR han sido esenciales para mantener la continuidad en los proyectos de ingeniería imperial, desde la Estrella de la Muerte hasta los sistemas de escudos planetarios en Scarif y Hoth.

Para más información sobre ADR:

- [Michael Nygard – Documenting Architecture Decisions](https://cognitect.com/blog/2011/11/15/documenting-architecture-decisions.html)  
- [Repositorio de Plantillas ADR en GitHub](https://github.com/joelparkerhenderson/architecture-decision-record)
