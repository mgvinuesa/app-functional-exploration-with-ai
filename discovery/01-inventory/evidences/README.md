# Índice de evidencias del inventario

Evidencias basadas en snapshots de accesibilidad obtenidos mediante Playwright MCP. Contexto común: Vikunja local, 2026-10-29; EV-01..85 corresponden principalmente a `rea_discovery_20261028b`, y EV-86..134 alternan la cuenta primaria y `rea_discovery_member_20261029` según el comentario de cada archivo. EV-05/06 y EV-08 en adelante están persistidos en este directorio; EV-01..04/07 se referencian por snapshots de origen. No se guardan credenciales ni tokens.

| ID | URL | Contexto y evidencia observada |
|---|---|---|
| EV-01 | `/` | Resumen: saludo al usuario; entrada «Add a task…», botón Añadir y ayuda de prefijos; accesos principales y globales; navegación lateral con Resumen, Próximas, Proyectos, Etiquetas, Equipos, filtros guardados y proyectos; tareas actuales con checkbox y enlace al detalle `/tasks/3`; atajos de teclado. Snapshot Playwright `page-2026-10-29T08-40-10-711Z.yml`. |
| EV-02 | `/tasks/by/upcoming` | Encabezado muestra intervalo 29-oct-2026 a 5-nov-2026 y mensaje de estado vacío. Snapshot `page-2026-10-29T08-41-03-223Z.yml`. |
| EV-03 | `/projects/5/36` | Tablero de «REA Discovery Project 20261028» con botón Filtros y Create a bucket; navegación lateral consistente. Snapshot `page-2026-10-29T08-40-33-253Z.yml`. |
| EV-04 | `/labels`, `/labels/new` | Listado ofrece «Nueva etiqueta»; diálogo Create a label con campos Título, Color y acciones Cancelar/Crear. Snapshots `page-2026-10-29T08-40-54-238Z.yml` y `page-2026-10-29T08-41-19-363Z.yml`. |
| EV-05 | `/teams`, `/teams/new` | Listado/alta de equipo sintético. Snapshot de edición persistido en `EV-05-team-edit.yml`. |
| EV-06 | `/teams/3/edit` | Edición y miembros del equipo sintético; campos nombre/descripción, Guardar/Eliminar, búsqueda y Añadir al equipo. Tabla muestra cuenta activa como `You / Admin`. Persistido en `EV-06-team-members.yml`. |
| EV-07 | `/user/settings/general` | Menú y navegación de cuenta; ajustes generales con categorías y preferencias descritas en FUN-18..FUN-22. Snapshot original `page-2026-10-29T08-43-34-937Z.yml`. |
| EV-08 | `/tasks/3` | Detalle de tarea y acciones visibles. `EV-08-task-detail.yml`. |
| EV-09–EV-10 | `/projects`, `/projects/new` | Listado de proyectos y formulario de alta con título, padre y color. |
| EV-11–EV-12 | `/projects/7/45` | Filtros, consulta inicial e información de operadores. |
| EV-13–EV-15 | `/projects/7/48` | Kanban, opciones del bucket, campo de alta de bucket sin confirmación observada. |
| EV-16–EV-19 | Vistas de `/projects/7` | Gantt, Tabla, Lista y opciones de ordenación. |
| EV-20–EV-24 | filtros guardados | Vista/menú/edición/alta y persistencia de filtro sintético. |
| EV-25–EV-27 | `/labels`, `/tasks/5` | Alta/edición de etiqueta sintética y asociación a tarea propia. |
| EV-28–EV-30 | `/tasks/5`, `/tasks/by/upcoming` | Selector de fecha, tarea sintética con fecha y Próximas poblada. |
| EV-31–EV-34 | proyecto y superficies globales | Ayuda de alta rápida, búsqueda, notificaciones y atajos. |
| EV-35–EV-36 | `/tasks/5` | Controles visibles de detalle; EV-36 muestra el selector de prioridad con sus opciones. |
| EV-37–EV-38 | `/user/settings/general`, `/user/settings/avatar` | Capturas transitorias con solo «Vikunja está cargando…»; no acreditan controles. Se sustituyen para descripción por EV-45 en Avatar. |
| EV-39–EV-41 | `/projects/7/48` | EV-39 conserva solo el indicador de carga; EV-40 muestra Kanban poblado y EV-41 muestra el campo de bucket aún abierto tras el intento. |
| EV-42 | `/about` | Diálogo Acerca de muestra versión `v2.7.1`. |
| EV-43 | `/user/settings/migrate` | Captura transitoria con indicador de carga; contenido acreditado por EV-48. |
| EV-44 | `/migrate/csv` | Captura transitoria con indicador de carga; contenido acreditado por EV-49. |
| EV-45 | `/user/settings/avatar` | Avatar cargado: Predeterminado, Iniciales, Gravatar, Marble, Subir y Guardar. No se cambió selección. PNG y snapshot persistidos. |
| EV-46 | `/user/settings/password-update` | Formulario con campos de contraseña vacíos y Guardar deshabilitado. No se ingresaron credenciales. PNG y snapshot persistidos. |
| EV-47 | `/user/settings/data-export` | Información de exportación y solicitud condicionada a contraseña. No se introdujo contraseña ni se solicitó copia. PNG y snapshot persistidos. |
| EV-48–EV-49 | `/user/settings/migrate`, `/migrate/csv` | Proveedores Vikunja Export, TickTick, WeKan, CSV y Planka; pantalla CSV con selector de archivo y mapeo. No se seleccionó archivo ni inició importación. PNG y snapshot persistidos. |
| EV-50–EV-53 | Proyecto `/projects/7` | EV-50 es captura parcial anterior; EV-51 menú contextual cargado, EV-52 formulario de edición, EV-53 configuración de vistas. PNG/snapshots persistidos cuando disponibles. |
| EV-54–EV-60 | Tarea propia `/tasks/5` | Detalle reabierto, opciones de progreso, búsqueda de asignación, entrada de relaciones, adjuntos, movimiento y primer acceso a recordatorios. EV-60 incluye PNG. |
| EV-61 | `/projects/7/48` | Prueba de pérdida de foco del campo de bucket; título descartado y tablero mantiene tres buckets. PNG y snapshot persistidos. |
| EV-62 | `/` | Tarea propia aparece en Tareas en Curso con control de estado y enlace al detalle; estado no cambiado. PNG y snapshot persistidos. |
| EV-63–EV-65 | Búsqueda global | Alcances `+` proyectos, `@` equipos y `*` etiquetas; sin modificar entidades. |
| EV-66 | Notificaciones | Estado vacío reconfirmado y enlace Atom Feed. PNG y snapshot persistidos. |
| EV-67 | `/user/settings/totp` | Pantalla solicita contraseña antes de inscripción; no se ingresó, no se generó secreto. PNG y snapshot persistidos. |
| EV-68–EV-69 | Ajustes del proyecto propio | Selección de fondo y opciones de compartir; no se eligió archivo ni se compartió. PNG y snapshots persistidos. |
| EV-70–EV-71 | `/projects/7/settings/views` | Edición de vista existente y formulario de nueva vista; no se guardó. PNG y snapshots persistidos. |
| EV-72 | `/tasks/5` | Snapshot persistido del control de búsqueda de asignación; no se mostró sugerencia al consultar por cuenta propia. |
| EV-73 | `/user/settings/email-update` | Formulario con correo nuevo y contraseña actual. Resumen DOM con valores omitidos; no se introdujeron. Incluye hora y cuenta observada. |
| EV-74 | `/user/settings/caldav` | Información de conexión CalDAV, tokens/contraseña como opciones de autenticación y botón de token dedicado. No se generó token ni se guardó URL/valor sensible; resumen DOM depurado. |
| EV-75 | `/user/settings/mcp` | Texto informativo de conexión de asistente a tareas/proyectos/etiquetas vía MCP. No se conectó servicio; resumen DOM con hora y cuenta. |
| EV-76 | `/user/settings/feeds` | Información de suscripción Atom Feed y autenticación con API token de permiso indicado. No se capturó URL/valor del feed ni se creó token; resumen DOM depurado. |
| EV-77 | `/user/settings/api-tokens` | Descripción de uso de tokens API y botón de alta; no se creó token. Resumen DOM depurado. |
| EV-78 | `/user/settings/sessions` | Descripción de sesiones y tabla con dispositivo, IP, última actividad y acciones; valor IP omitido. No se revocó sesión. |
| EV-79 | `/user/settings/webhooks` | Formulario de notificaciones con Target URL, Secret opcional, Basic Auth, eventos y creación; no se rellenó ni creó. Resumen DOM depurado. |
| EV-80 | `/user/settings/bots` | Descripción de bot API-only, campos Nombre de usuario/Name y botón CREATE BOT. No se creó bot. |
| EV-81 | `/user/settings/deletion` | Aviso de borrado permanente, solicitud de contraseña y botón de eliminación; se dejó vacío y no se confirmó. |
| EV-82 | `/tasks/5` | Selector de relaciones abierto: diez tipos, sin elegir tipo ni crear relación. Snapshot y PNG; comentario incluye URL, cuenta y hora UTC. |
| EV-83 | `/tasks/5` | «Add a reminder…» abierto con presets hasta 30 días, Personalizado y Fecha y hora; no se añadió recordatorio. Snapshot/PNG con metadatos de hora y cuenta. |
| EV-84 | `/projects/7/settings/webhooks` | Modal vacío con URL, secreto opcional, Basic Auth y eventos de proyecto/tarea; Cancelar sin guardar. Snapshot/PNG con metadatos; no se creó endpoint. |
| EV-85 | `/projects/7/settings/share` | Ayuda emergente explica que enlaces compartidos permiten acceso a personas sin cuenta Vikunja; sin crear enlace. Snapshot/PNG con metadatos. |
| EV-86 | `/` | Resumen en sesión aislada de segunda cuenta sintética sin participación previa; no se muestra rol global. |
| EV-87 | `/teams/3/edit` | Cuenta primaria añade la cuenta secundaria como miembro al equipo sintético. |
| EV-88 | `/projects/7/settings/share` | Cuenta primaria comparte el proyecto sintético y selecciona Read only. |
| EV-89–EV-92 | `/`, `/projects/7/45`, `/projects/7/48`, `/tasks/5` | Segunda cuenta con Read only: proyecto y vistas visibles; control de estado deshabilitado, sin alta de tarea ni menú de configuración. |
| EV-93 | `/teams/3/edit` | Segunda cuenta como miembro; lista de miembros y acción «Abandonar equipo», sin controles de edición/alta. |
| EV-94–EV-97 | `/projects/7/45`, `/tasks/5`, `/tasks/6` | Read & write: controles de alta/cambio habilitados, tarea sintética creada por segunda cuenta y detalle. |
| EV-98–EV-99 | `/projects/7/45`, `/projects/7/settings/edit` | Admin temporal del proyecto: menú contextual y formulario de edición visibles; no se guardó. |
| EV-100–EV-101 | `/teams/3/edit` | Admin temporal del equipo: control de rol desde primaria y formulario/gestión de miembros desde secundaria; no se modificó la cuenta primaria Admin ni se guardó el equipo. |
| EV-102 | `/tasks/5` | Cuenta primaria asigna la tarea sintética al segundo usuario. |
| EV-103 | `/register` | Formulario público de alta en contexto aislado, vacío antes de crear la cuenta; no contiene credenciales. |
| EV-104 | `/teams/3/edit` | Vista final de la segunda cuenta restaurada a miembro del equipo. |
| EV-105 | `/tasks/5` | Confirmación de asignación desde sesión primaria. |
| EV-106 | `/tasks/5` | Desde segunda cuenta, detalle muestra asignación propia y acciones de tarea con Read & write. |
| EV-107 | `/projects/7/45` | Estado final Read & write: entrada para añadir tarea y checkboxes activos, incluyendo tarea creada por la segunda cuenta. |
| EV-108 | `/projects/7/45` | Panel de la segunda cuenta muestra dos notificaciones no leídas por alta en equipo y asignación de tarea, controles de limpiar/marcar leído y enlace Atom Feed; no se activaron controles. |
| EV-109 | `/projects/7/settings/share` | Selector de la cuenta primaria, creadora del proyecto, confirma permiso directo Read & write y lista de equipos vacía. |
| EV-110 | `/projects/7/45` | Menú del proyecto abierto por secundaria con Read & write: opciones de gestión excepto Eliminar. No se ejecutó ninguna opción. |
| EV-111–EV-112 | `/projects/7/settings/share` | Retirada del permiso directo: EV-111 confirma que la UI solicita confirmación; EV-112 muestra usuario fuera de la lista tras confirmar, antes de compartir con equipo. |
| EV-113–EV-116 | `/projects/7/settings/share` | Búsqueda UI, resultados de equipos sintéticos y selección del equipo de prueba. |
| EV-117 | `/projects/7/settings/share` | Proyecto agregado al equipo sintético; selector del equipo muestra Read only seleccionado; concesión directa ausente. |
| EV-118 | `/projects/7/45` | Miembro de equipo sin permiso directo ve proyecto/dos tareas; checkbox deshabilitado y sin entrada Add a task. |
| EV-119 | `/tasks/5` | Miembro con acceso Read only por equipo ve detalle/fecha sin acciones de gestión. |
| EV-120–EV-121 | `/projects/new` | Formulario y alta UI del proyecto propio `REA URL Access Project 20261029`. |
| EV-122–EV-123 | `/teams/new` | Formulario y alta UI del equipo propio `REA URL Access Team 20261029`, sin miembro secundario. |
| EV-124 | `/projects/9/61` | Sesión secundaria abre URL directa del proyecto no compartido; la UI muestra “You don't have the permission to see this”. |
| EV-125 | `/teams/4/edit` | Sesión secundaria abre URL directa del equipo al que no pertenece; la UI muestra el mismo aviso de permiso. |
| EV-126–EV-127 | `/projects/7/settings/share` | Estado de equipo compartido antes de restauración y diálogo de confirmación para retirarlo; el aviso enumera posible pérdida de asignaciones, suscripciones y webhooks de quienes pierdan acceso. No se verificaron esos efectos. |
| EV-128–EV-132 | `/projects/7/settings/share` | Búsqueda/selección y alta de la concesión directa de usuario, permiso Read only por defecto tras volver a compartir. |
| EV-133 | `/projects/7/settings/share` | Estado final restaurado: Read & write directo, sin equipo compartido. |
| EV-134 | `/projects/7/45` | Secundaria vuelve a abrir el proyecto con la concesión directa Read & write restaurada. |
| EV-135 | `/projects/7/settings/share` | Baseline inicial de esta revisión: permiso directo Read & write y sin equipo compartido. |
| EV-136–EV-139 | `/projects/7/settings/share` | Búsqueda UI del equipo propio y selección antes de conceder permiso. |
| EV-140–EV-141 | `/projects/7/settings/share` | Equipo compartido; selector Read only por defecto y luego Read & write seleccionado. |
| EV-142–EV-143 | `/projects/7/settings/share` | Retirada temporal de permiso directo; EV-143 confirma la lista directa vacía y equipo Read & write seleccionado. |
| EV-144 | `/projects/7/45` | Secundaria miembro por equipo Read & write; alta de tarea y checkboxes habilitados, dos tareas visibles. |
| EV-145 | `/projects/7/45` | Snapshot intermedio en el que se abrió por error el menú de filtro guardado; no se ejecutó acción. |
| EV-146 | `/projects/7/45` | Menú de proyecto con permiso de equipo Read & write: opciones de gestión excepto Eliminar. |
| EV-147 | `/tasks/5` | Detalle con permiso de equipo Read & write; controles de gestión de tarea visibles, sin cambios. |
| EV-148–EV-149 | `/projects/7/settings/share` | Selector de equipo confirma Read & write y luego Admin con la lista directa vacía. |
| EV-150 | `/projects/7/45` | Secundaria miembro por equipo Admin; alta de tarea y checkboxes habilitados. |
| EV-151 | `/projects/7/45` | Menú de proyecto bajo permiso de equipo Admin; incluye Eliminar, que no se ejecutó. |
| EV-152 | `/tasks/5` | Detalle con permiso de equipo Admin; controles de gestión visibles, sin cambios. |
| EV-153–EV-156 | `/projects/7/settings/share` | Selector Admin y retirada de concesión de equipo; ambas listas quedan vacías antes de restaurar el acceso directo. |
| EV-157–EV-159 | `/projects/7/settings/share` | Búsqueda y selección UI de la cuenta secundaria para restaurar la concesión directa. |
| EV-160–EV-161 | `/projects/7/settings/share` | Permiso directo Read only por defecto y luego Read & write seleccionado; lista de equipo vacía. |
| EV-162 | `/projects/7/45` | Secundaria vuelve a abrir el proyecto tras restaurar el permiso directo Read & write. |

Los snapshots EV-01..04/07 originales permanecen en `.playwright-mcp`; EV-05/06 y EV-08..EV-162 están guardados con nombres estables en este directorio. EV-73..EV-81 contienen resúmenes DOM depurados, no capturas visuales; EV-82..EV-162 tienen metadata de observación. En EV-37/38/39/43/44 solo consta una pantalla transitoria de carga; no atribuirles contenido funcional. Las evidencias de roles no incluyen credenciales.
