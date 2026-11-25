# EVENTIA · Prototipo funcional (Práctica 3)

Prototipo de frontend de **EVENTIA**, el sistema de gestión de eventos, espacios y participación universitaria que estamos desarrollando como proyecto semestral de Ingeniería de Software I (FCC, BUAP).

Esto **no es el sistema completo**. Es una primera porción del frontend con datos inventados, que hicimos para probar en pantalla algunas reglas del SRS antes de pasar a construir el sistema real. No tiene servidor, base de datos, inicio de sesión institucional ni envío de correos.

## Datos del proyecto

| | |
|---|---|
| Caso maestro | EVENTIA |
| Equipo | Eventia |
| Materia | Ingeniería de Software I |
| Docente | Dr. Luis Yael Méndez Sánchez |
| Modelo de proceso | RUP con un ciclo de prototipado en la Elaboración |
| Fase a la que corresponde este prototipo | Elaboración, iteración 2 |

**Integrantes**

- Grecia Alondra Barojas Reyes
- Jaime Alexis Hernández Franco
- Araceli Ramírez Fabián
- Luz María Sánchez Flores

## Qué se puede hacer en el prototipo

Tiene cuatro pantallas. Se cambia entre ellas con los botones de la barra de arriba, y el rol activo cambia según la pantalla (Participante, Organizador o Coordinación).

| Pantalla | Figma (Práctica 2) | Qué se puede probar |
|---|---|---|
| P-01 Catálogo de eventos | PNT-02 | Buscar por texto y filtrar por tipo y modalidad. Registrarse en un evento; si ya no hay cupo, entrar a la lista de espera. No deja registrarse dos veces en el mismo evento (RN-009, RN-010). |
| P-02 Mis registros | PNT-05 | Ver el estado de cada registro y cancelarlo. Pide confirmación y, si el registro estaba confirmado, el lugar se libera (RN-011). Nadie de la lista de espera sube solo, porque en la v1.0 eso lo hace el organizador a mano (DEC-01). |
| P-03 Solicitar evento | PNT-06 / PNT-07 | Llenar una solicitud. Revisa campos obligatorios, que la hora de fin sea después de la de inicio (RD-05) y que el cupo no pase la capacidad del espacio (RN-007). Al enviarla se genera un folio. |
| P-04 Bandeja de revisión | PNT-09 | La solicitud nueva aparece aquí. Para devolver o rechazar hay que escribir un motivo (RD-07). Si una solicitud tiene traslape, el botón «Aprobar» se bloquea. |

> El traslape de la bandeja viene ya marcado en los datos de ejemplo (solicitud SOL-2026-041). El prototipo no lo calcula; eso le toca al servidor en la fase de Construcción (RF-009).

## Cómo abrirlo

No hay que instalar nada.

1. Descargar el repositorio (botón **Code → Download ZIP**) o clonarlo.
2. Abrir `eventia/index.html` en el navegador (Chrome, Edge, Firefox o Safari).

Si se prefiere servirlo de forma local:

```bash
cd eventia
python -m http.server 8000
# luego abrir http://localhost:8000
```

Los datos viven en la memoria del navegador, así que al recargar la página todo vuelve a como estaba al inicio.

## Tecnología

- HTML, CSS y JavaScript sin frameworks ni librerías.
- Todo está en un solo archivo (`eventia/index.html`), así que no hay paso de compilación.
- Colores tomados de la guía de estilo del DAS/SDD (azul institucional `#15294B`).

## Estructura del repositorio

```
├── README.md
├── eventia/
│   └── index.html          prototipo (HTML + CSS + JS)
└── docs/
    ├── evidencia-ia.md     prompts, iteraciones y correcciones
    ├── trazabilidad.md     pantalla ↔ requisito ↔ componente
    └── capturas/           capturas de las cuatro pantallas
```

## Uso de inteligencia artificial

La primera versión del código la generamos con **Gemini** (noviembre de 2026), en dos iteraciones. Después la revisamos contra el SRS y corregimos varias cosas a mano. Por ejemplo, la IA subía automáticamente al primero de la lista de espera y mostraba nombres de inscritos en el catálogo público, y las dos cosas van en contra del SRS. Para revisar el código y hacer las correcciones finales también usamos **Claude**.

Los prompts completos, lo que salió en cada iteración y lo que cambiamos nosotros están en [`docs/evidencia-ia.md`](docs/evidencia-ia.md).

No usamos datos personales reales en ninguna herramienta. Todos los nombres, eventos y folios son inventados.

## Lo que falta

- Seis pantallas del Figma que todavía no están: acceso institucional (PNT-01), detalle del evento (PNT-03), registro confirmado (PNT-04), panel del organizador (PNT-08), calendario de espacios (PNT-10) y registro de bloqueos (PNT-11).
- El backend (servidor y base de datos), la detección real de traslapes y bloqueos, y la promoción manual desde la lista de espera.
- La conexión con el servicio institucional de autenticación y con el correo.

Todo esto está planeado para las iteraciones de Construcción en el Gantt del documento de la Práctica 3.

## Documentos relacionados

- Práctica 1 · SRS v1.0 de EVENTIA
- Práctica 2 · DAS/SDD v1.0 y prototipo en Figma
- Práctica 3 · Proceso de desarrollo y prototipo funcional (documento donde se describe este repositorio)
