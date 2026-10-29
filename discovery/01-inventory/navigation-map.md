# Mapa de navegación observado

Observación: 2026-10-29. Aplicación local `http://localhost:3456`; sesiones sintéticas `rea_discovery_20261028b` y `rea_discovery_member_20261029` en contextos aislados.

Este mapa identifica rutas recorridas, no permisos generales de acceso. Los destinos iniciales y ajustes se observaron principalmente con la cuenta primaria; las rutas de proyecto/equipo compartidos se repitieron con la secundaria bajo permisos directos y por equipo diferentes. Para atribuir cada capacidad a una sesión, rol y recurso concretos, consulta `roles.md`, `user-stories.md` y la EV citada.

| Origen / área | Destino o acción observada | URL observada | Evidencia |
|---|---|---|---|
| Barra principal | Vikunja home / Resumen | `/` | EV-01 |
| Acceso público sin sesión | Formulario de registro de cuenta sintética | `/register` | EV-103, EV-86 |
| Barra principal | Búsqueda / acción rápida | Botón | EV-01 |
| Barra principal | Notificaciones | Botón | EV-01 |
| Barra principal | Menú de cuenta | Botón con nombre de usuario | EV-01 |
| Navegación lateral | Próximas | `/tasks/by/upcoming` | EV-02 |
| Navegación lateral | Proyectos | `/projects` | EV-03 |
| Navegación lateral | Etiquetas | `/labels` | EV-04 |
| Navegación lateral | Equipos | `/teams` | EV-05 |
| Navegación lateral | Filtros guardados | `/projects/-5`, `/projects/-6`, `/projects/-7` | EV-01, EV-09, EV-24 |
| Navegación lateral | Bandeja de entrada/proyectos | `/projects/4`, `/projects/5`, `/projects/6`, `/projects/7` | EV-01, EV-09 |
| Etiquetas | Nueva etiqueta (diálogo) | `/labels/new` | EV-04 |
| Equipos | Crear equipo (diálogo) | `/teams/new` | EV-05 |
| Proyectos | Listado y alta | `/projects`, `/projects/new` | EV-09–EV-10 |
| Proyecto sintético | Lista, Gantt, Tabla y Kanban | `/projects/7/45`, `/projects/7/46`, `/projects/7/47`, `/projects/7/48` | EV-13, EV-16–EV-18 |
| Proyecto | Filtros, ayuda de consulta y ordenación | `/projects/7/45`, `/projects/7/48` | EV-11–EV-12, EV-19 |
| Proyecto Kanban | Opciones bucket y alta con Enter/pérdida de foco sin persistencia | `/projects/7/48` | EV-13–EV-15, EV-39–EV-41, EV-61 |
| Filtros guardados | Ver/editar filtro sintético y crear uno | `/projects/-6`, `/projects/-6/settings/edit`, `/filters/new`, `/projects/-7/49` | EV-20–EV-24 |
| Etiquetas | Crear, listar, editar y asociar a tarea sintética | `/labels/new`, `/labels`, `/tasks/5` | EV-25–EV-27 |
| Tarea sintética | Detalle y fecha límite; visible en Próximas | `/tasks/5`, `/tasks/by/upcoming` | EV-27–EV-30 |
| Global de página | Atajos de teclado | Botón persistente | EV-01 |
| Proyecto propio | Menú contextual, edición, vistas, fondo y compartir | `/projects/7/settings/edit`, `/projects/7/settings/views`, `/projects/7/settings/background`, `/projects/7/settings/share` | EV-51–EV-53, EV-68–EV-71 |
| Proyecto propio | Vistas Lista, Gantt, Tabla, Kanban; abrir edición y alta de vista sin guardar | `/projects/7/settings/views` | EV-53, EV-70–EV-71 |
| Proyecto propio | Webhooks: formulario de URL, secreto opcional, Basic Auth y eventos | `/projects/7/settings/webhooks` (modal desde menú del proyecto) | EV-84 |
| Proyecto propio | Ayuda de enlace compartido | `/projects/7/settings/share` (tooltip en «¿Qué es un enlace compartido?») | EV-69, EV-85 |
| Proyecto propio | Abrir tarea propia desde proyecto | `/tasks/5` | EV-54–EV-60, EV-72 |
| Menú de cuenta | Ajustes | `/user/settings/general` | EV-07 |
| Menú de cuenta | Atajos de teclado | Botón | EV-07 |
| Menú de cuenta | Acerca de | `/about` | EV-42 |
| Ajustes | General, Avatar, cambio de contraseña, TOTP y exportación; no se enviaron formularios ni se introdujeron credenciales | `/user/settings/general`, `/user/settings/avatar`, `/user/settings/password-update`, `/user/settings/totp`, `/user/settings/data-export` | EV-07, EV-45–EV-47, EV-67 |
| Ajustes | Email, CalDAV, MCP, Atom Feed, API Tokens, sesiones, webhooks de cuenta, bots y eliminación; inspección sin valores ni operaciones | `/user/settings/email-update`, `/user/settings/caldav`, `/user/settings/mcp`, `/user/settings/feeds`, `/user/settings/api-tokens`, `/user/settings/sessions`, `/user/settings/webhooks`, `/user/settings/bots`, `/user/settings/deletion` | EV-73–EV-81 |
| Ajustes / importación | Proveedores de migración y formulario CSV cargados; no se eligió archivo | `/user/settings/migrate`, `/migrate/csv` | EV-48–EV-49 |
| Búsqueda | Modos de alcance proyectos/equipos/etiquetas | Diálogo global | EV-63–EV-65 |
| Notificaciones de las cuentas primaria y secundaria | Panel vacío en primaria y avisos no leídos tras alta/asignación en secundaria; no se marcaron ni limpiaron | Panel global | EV-66, EV-108 |
| Equipo sintético, secundaria miembro y Admin temporal | Lista de miembros como miembro; formulario y controles de gestión como Admin | `/teams/3/edit` | EV-93, EV-100–EV-104 |
| Proyecto propio compartido por la primaria | Formulario de compartir con permiso directo seleccionable Read only, Read & write o Admin para la secundaria | `/projects/7/settings/share` | EV-88, EV-109, EV-133 |
| Proyecto compartido con la secundaria mediante permiso directo | Lista, tablero y detalle observados con permisos directos Read only, Read & write y Admin en momentos distintos | `/projects/7/45`, `/projects/7/48`, `/tasks/5` | EV-89–EV-99, EV-105–EV-107 |
| Proyecto compartido con equipo | Selector encuentra equipo propio; permiso Read only aparece en fila de equipo; miembro ve proyecto/tareas en modo lectura cuando la concesión directa se retira temporalmente | `/projects/7/settings/share`, `/projects/7/45`, `/tasks/5` | EV-109, EV-112, EV-115–EV-119, EV-126–EV-134 |
| Proyecto con permisos de equipo Read & write/Admin | Miembro ve alta/checkboxes activos; con Read & write menú sin Eliminar, con Admin menú con Eliminar; detalle de tarea muestra controles de gestión en ambos niveles | `/projects/7/settings/share`, `/projects/7/45`, `/tasks/5` | EV-135–EV-153 |
| Menú de proyecto de la secundaria con permiso directo Read & write | Opciones de edición/vistas/fondo/compartir/duplicar/archivar/suscripción/webhooks/crear; no se ve Eliminar | `/projects/7/45` | EV-110 |
| Proyecto/equipo sintéticos sin compartir | Alta UI y acceso por URL directa como secundaria; la UI muestra aviso de falta de permiso | `/projects/9/61`, `/teams/4/edit` | EV-120–EV-125 |
