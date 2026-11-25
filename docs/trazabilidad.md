# Trazabilidad diseño ↔ implementación

Relación entre lo que diseñamos en el DAS/SDD v1.0 (componentes y pantallas de Figma) y lo que de verdad quedó en el código del prototipo (`eventia/index.html`). La versión completa está en la sección 9 del documento de la Práctica 3.

Estados:
- **Implementado:** funciona en el prototipo con datos de ejemplo.
- **Simulado:** se ve en pantalla, pero no hay lógica real detrás.
- **Pendiente:** no está en el prototipo.

## Por componente

| Componente (DAS/SDD) | Dónde está en el prototipo | Funciones del código | Requisitos y reglas | Estado |
|---|---|---|---|---|
| COMP-01 Autenticación y permisos | Rol activo en la barra superior; cambia según la pantalla | `cambiarVista()` | RF-001, RF-002 | Simulado (no hay inicio de sesión; PNT-01 pendiente) |
| COMP-02 Gestión de eventos | P-01 Catálogo (PNT-02), P-03 Solicitar evento (PNT-06/07) y P-04 Bandeja (PNT-09) | `renderizarCatalogo()`, `validarFormularioSolicitud()`, `enviarSolicitud()`, `dictaminar()` | RF-003, RF-004, RF-009, RF-014, RD-05, RD-07 | Implementado en frontend |
| COMP-03 Gestión de espacios | Lista fija de espacios y su capacidad en P-03; advertencia de traslape en P-04 | `inicializarSelectEspacios()`, `renderizarBandeja()` | RF-008, RF-009, RF-020, RN-004, RN-007 | Simulado (lista estática; el traslape está precargado en SOL-2026-041; sin calendario ni bloqueos) |
| COMP-04 Inscripciones y lista de espera | P-01 Catálogo (PNT-02) y P-02 Mis registros (PNT-05) | `inscribirse()`, `cancelarRegistro()`, `renderizarRegistros()` | RF-005, RF-006, RF-015, RF-016, RF-018, RF-019, RN-009, RN-010, RN-011, RN-017 | Implementado en frontend |
| COMP-05 Notificaciones | Aviso en P-02 sobre el correo (FAL-02) y mensajes en pantalla | `mostrarAlerta()` | RF-007, RF-021 | Simulado (no se envían correos) |
| COMP-06 Bitácora | Mensaje «asentada en bitácora» al dictaminar en P-04 | `dictaminar()` (solo el mensaje) | RF-022 | Simulado (no se guarda ni se consulta un historial) |
| COMP-07 Reportes | — | — | RF-023 | Pendiente |
| COMP-08 Administración de catálogos | Lista fija de espacios (`ESPACIOS`) | — | RF-024 | Pendiente |

## Pantallas de Figma

| Pantalla Figma | En el prototipo | Estado |
|---|---|---|
| PNT-01 Acceso institucional | — | Pendiente |
| PNT-02 Catálogo de eventos | P-01 | Implementado |
| PNT-03 Detalle del evento | — (los datos se ven en la tarjeta del catálogo) | Pendiente |
| PNT-04 Registro confirmado | Mensaje de éxito en P-01 | Simulado |
| PNT-05 Mis registros | P-02 | Implementado |
| PNT-06 Solicitud de evento | P-03 | Implementado |
| PNT-07 Solicitud con errores | P-03 (mensajes de error del formulario) | Implementado |
| PNT-08 Panel del organizador | — | Pendiente |
| PNT-09 Bandeja de revisión | P-04 | Implementado |
| PNT-10 Calendario de espacios | — | Pendiente |
| PNT-11 Registro de bloqueo | — | Pendiente |

**Resumen:** de las 11 pantallas, 5 están implementadas (PNT-02, 05, 06, 07 y 09), 1 está simulada (PNT-04) y 5 están pendientes.
