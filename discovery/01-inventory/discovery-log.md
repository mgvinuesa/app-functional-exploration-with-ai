# Registro de descubrimiento

## 2026-10-29 — Inicialización y recorrido exploratorio

- Se revisó la documentación existente; `discovery/` no contenía documentos previos.
- Se observó sesión ya autenticada `rea_discovery_20261028b`, sin exponer credenciales.
- Se recorrieron Resumen, proyecto existente, Próximas, Etiquetas y Equipos mediante rutas y navegación observadas.
- Se abrieron los formularios `/labels/new` y `/teams/new`. Diálogo de etiqueta mostró Título y Color; diálogo de equipo mostró Nombre del Equipo.
- Se creó desde el diálogo el equipo sintético `REA Discovery Team 20261029`; ruta resultante `/teams/3/edit`, mensaje visible «El equipo fue creado con éxito».
- La edición del equipo expone nombre, descripción enriquecida, Guardar, Eliminar el equipo; sección Miembros del Equipo con búsqueda de usuario, Añadir al equipo y fila `rea_discovery_20261028b / You / Admin`. No se añadió otra cuenta.
- Un primer intento fue cancelado por una referencia de control obsoleta; el alta se repitió con snapshot renovado y se confirmó exitosamente.
- Se identificaron búsqueda/acción rápida, notificaciones, menú de cuenta y atajos de teclado; sus paneles quedan pendientes.
- No se realizaron eliminaciones, cambios sensibles ni operaciones sobre terceros.
- Se registró la creación sintética en `synthetic-data-activity.md`.
- Se abrió el menú de cuenta: ofrece Ajustes, Atajos de teclado, Acerca de y Cerrar sesión. Se visitó Ajustes Generales sin modificar controles.
- La pantalla general agrupa preferencias personales; proyectos/tareas; localización; apariencia/conducta; privacidad. Se observaron vistas predeterminadas (First View, Lista, Gantt, Tabla, Kanban), preferencias de fecha/idioma, modo de adición rápida y relaciones, además de secciones de seguridad, exportación/migración, integraciones, sesiones, tokens y eliminación de cuenta. Estas secciones se registran como accesos visibles, no como operaciones ejecutadas.
- Limitación: los clics por `aria-ref` expiraban en algunos cambios de vista; la automatización y el DOM snapshot fueron las únicas herramientas utilizadas.

## 2026-10-29 — Revisión incremental 1

- Se reabrió `/tasks/3` y se documentó el detalle con sus controles y grupos de acciones (EV-08). Se inspeccionó el detalle de la tarea sintética `/tasks/5`; etiqueta y fecha límite se relacionaron con esa tarea (EV-27–EV-30).
- Se creó el proyecto sintético `REA Inventory Project 20261029`, se recorrieron sus vistas Lista, Gantt, Tabla y Kanban, y se observaron filtros, ayuda de consulta y ordenación (EV-09–EV-19).
- Se creó el filtro sintético `REA Inventory Filter 20261029`; se inspeccionaron vista, menú de configuración, edición y formulario de alta (EV-20–EV-24).
- Se creó la etiqueta sintética `REA Inventory Label 20261029` y se asoció a la tarea sintética (EV-25–EV-27).
- Próximas se inspeccionó poblada con una tarea propia fechada; se observó selector de rango y controles para tareas sin fecha/vencidas (EV-30).
- Se abrieron búsqueda/acción rápida, notificaciones y atajos; la búsqueda con texto exacto de la tarea no mostró resultados, mientras texto genérico mostró sugerencias y resultados (EV-31–EV-34).
- Kanban mostró opciones de buckets y el campo de alta de nuevo bucket. Dos intentos de confirmación por Enter dejaron el campo abierto sin mensaje ni persistencia visible; se documentó como límite reproducible (EV-14–EV-15, EV-39–EV-41).
- Se volvieron a abrir ajustes generales, se inspeccionaron opciones de avatar sin guardar cambios y se visitó Acerca de, que muestra `v2.7.1` (EV-37–EV-38, EV-42).
- Se abrió la pantalla de importación desde ajustes y la vista CSV; se identificaron proveedores y selector de archivo sin seleccionar ni enviar datos (EV-43–EV-44).
- En reintentos posteriores, los detalles `/tasks/5` y `/tasks/3` conservaron el indicador «Vikunja está cargando…» aun tras esperar; el contenido de detalle no quedó accesible de nuevo en esta ronda. No se observaron errores de consola en la consulta previa.
- Se persistieron en `evidences/` los snapshots nuevos y disponibles EV-05/06. No se alteraron datos de otros usuarios ni configuraciones sensibles. DQ-13 continúa bloqueada por no disponer de segundo usuario autorizado.

## 2026-10-29 — Revisión incremental 2

- Tras renovar snapshots, se reabrió la tarea propia `/tasks/5` desde el proyecto y desde Resumen; el detalle cargó. Se inspeccionaron progreso, búsqueda de asignación, entrada de relación con selector de tipo cerrado, movimiento, entrada de adjuntos y control para añadir recordatorios. No se aplicaron valores ni selecciones; la búsqueda de asignación por la cuenta actual no mostró sugerencias (EV-54–EV-60, EV-62, EV-72).
- En el Kanban propio, el título de bucket de prueba se descartó al perder foco mediante clic en Filtros; se cerró el panel y se comprobó que el tablero seguía mostrando To-Do, Doing y Done (EV-61).
- En el proyecto propio se inspeccionó el menú contextual, edición, selección de fondo, compartir y ajustes de vistas; se abrieron formularios de editar/crear vista sin guardar ni activar acciones de archivo, eliminación, compartir o webhook (EV-51–EV-53, EV-68–EV-71).
- Se reabrieron Avatar, cambio de contraseña, exportación, importación, CSV y TOTP tras esperar carga. Las pantallas cargadas muestran opciones de Avatar, proveedores y mapeo CSV, formularios de contraseña/exportación y puerta de contraseña para TOTP. No se introdujeron credenciales, no se generó secreto, no se eligió archivo y no se inició ninguna operación (EV-45–EV-49, EV-67).
- Se ampliaron los modos de búsqueda mediante `+` (proyectos), `@` (equipos) y `*` (etiquetas), y se reconfirmó el panel vacío de notificaciones (EV-63–EV-66).
- EV-37/38/39/43/44 son capturas transitorias de carga y no prueban el contenido de pantalla; las referencias funcionales se actualizaron a los snapshots posteriores cargados EV-45–EV-49 y EV-61/66.
- DQ-13 sigue bloqueada por ausencia de segunda cuenta autorizada. Chrome continúa abierto; no se modificaron ajustes sensibles ni datos ajenos.

## 2026-10-29 — Revisión incremental 3

- Desde los enlaces de Ajustes Generales se abrieron email, CalDAV, MCP, Atom Feed, API Tokens, Sessions, Webhook Notifications, Bot Users y eliminación de cuenta. Se conservaron EV-73–EV-81 con URL, título, controles y hora UTC; los resúmenes excluyen valores de campos, dirección de correo, IP y cadenas largas que pudieran contener credenciales o tokens.
- Email muestra campos de correo nuevo y contraseña actual; CalDAV/Atom Feed describen autenticación por contraseña o token y accesos de feed; MCP describe conexión mediante protocolo MCP; API Tokens presenta información y botón de alta; Sessions muestra dispositivos, IP, última actividad y acciones de revocación (IP omitida en evidencia); Webhook Notifications muestra URL, secreto opcional, Basic Auth y eventos; Bot Users explica bots API-only con campos de nombre de usuario/nombre; eliminación advierte que es permanente y solicita contraseña. No se introdujeron valores ni se activaron acciones. La eliminación queda limitada por su puerta de contraseña y carácter destructivo.
- En el detalle propio `/tasks/5` se abrió el selector de tipo de relación y se registraron diez opciones (EV-82); se abrió «Add a reminder…» con presets y opciones personalizadas/fecha-hora (EV-83), sin elegir nada.
- El menú del proyecto sintético abrió un formulario de Webhooks con URL, secreto opcional, Basic Auth y eventos de proyecto/tarea; se cerró con Cancelar vacío (EV-84). En Compartir se mostró el tooltip de ayuda, que describe el uso de enlaces con personas sin cuenta (EV-85). No se crearon endpoints ni enlaces públicos.
- DQ-02 y DQ-16 quedaron DONE para estas superficies informativas; DQ-17 pasó a DONE. DQ-13 permanece BLOCKED por ausencia de segunda cuenta autorizada. No se avanzó a análisis funcional ni se cerró Chrome.

## 2026-10-29 — Reanudación autorizada de exploración de roles

- Se releeyeron las instrucciones vigentes de descubrimiento y restricciones; ambas autorizan registrar cuentas sintéticas por UI y configurar roles/permisos en recursos sintéticos propios. No se consultaron fuentes ni backend.
- En un contexto aislado se completó el alta de `rea_discovery_member_20261029` por `/register`. El formulario público aceptó la creación sin paso de confirmación de correo observado; no se registraron credenciales, dirección ni secretos (EV-86, EV-103).
- La cuenta primaria añadió a la secundaria al equipo `REA Discovery Team 20261029`; se observó la vista de miembro y la vista temporal Admin. El permiso de equipo se restauró a miembro (EV-87, EV-93, EV-100–EV-104).
- Se compartió `REA Inventory Project 20261029` con permisos Read only, Read & write y Admin para comparar el acceso en lista, Kanban, detalle y ajustes. Admin abrió el menú y formulario de edición sin guardar; el estado final se restauró a Read & write (EV-88–EV-99, EV-107).
- Con Read & write la cuenta secundaria creó `REA Member Write Task 20261029`. La cuenta primaria asignó a esa cuenta la tarea sintética `REA Inventory Task 20261029`; la asignación se observó desde las dos sesiones (EV-96–EV-97, EV-102, EV-105–EV-106).
- DQ-13 se actualizó a DONE. `roles.md`, cobertura, navegación, árbol, historias, actividad de datos e índice de evidencias se actualizaron; estado final en la app: equipo como miembro y proyecto Read & write. No se obtuvo ni intentó un rol global administrativo.
- No se guardaron cambios sensibles ni se ejecutaron eliminaciones, archivo, creación de integraciones externas o importación. Chrome se mantiene abierto y en la sesión secundaria del proyecto sintético.
- La revisión del panel de notificaciones de la cuenta secundaria reveló dos avisos no leídos generados por la incorporación al equipo y la asignación de tarea, junto con «Clear notifications» y «Mark all notifications as read»; no se ejecutaron esas acciones (EV-108).

## 2026-10-29 — Auditoría incremental de permisos y rutas

- Se abrió el selector directo del propietario y se confirmó Read & write para la secundaria. En la sesión secundaria con ese permiso se abrió el menú de proyecto: están disponibles Editar, Views, Background settings, Compartir, Duplicar, Archivar, Suscribirse, Webhooks y Crear proyecto; no aparece Eliminar, que estaba presente en el snapshot Admin. No se ejecutó ninguna acción (EV-109–EV-110).
- En el proyecto sintético se retiró temporalmente el permiso directo, con confirmación UI, y se compartió por UI con el equipo `REA Discovery Team 20261029`. El selector del equipo mostró Read only por defecto. Como miembro, la secundaria vio el proyecto y dos tareas, con checkboxes deshabilitados y sin entrada de alta; el detalle de la tarea propia permaneció visible en solo lectura (EV-111–EV-119).
- Para aislar acceso sin participación, se crearon por UI el proyecto `REA URL Access Project 20261029` y el equipo `REA URL Access Team 20261029`, sin compartirlos ni añadir la secundaria. Sus rutas observadas directas `/projects/9/61` y `/teams/4/edit`, abiertas en la sesión secundaria, mostraron el aviso UI “You don't have the permission to see this” (EV-120–EV-125). No se infiere código de estado ni una regla universal.
- Se restauró el baseline del proyecto principal: retirada la concesión de equipo, compartido directamente con la secundaria y restaurado Read & write; selector de propietario y vista de secundaria confirman ese estado (EV-126–EV-134). La secundaria sigue como miembro del equipo original; los recursos nuevos de control permanecen sin compartir.
- DQ-18, DQ-19 y DQ-20 quedaron DONE. Se actualizaron backlog, roles, cobertura, árbol, historias, navegación, datos sintéticos, índice y observaciones técnicas. Chrome permanece abierto en sesión secundaria; no se avanzó a análisis ni especificación.

## 2026-10-29 — Auditoría final de permisos por equipo

- Se revisó la auditoría incremental vigente, que identificaba los permisos de equipo Read & write y Admin seleccionables pero no explorados. Se mantuvo la secundaria como miembro y se retiró su permiso directo del proyecto 7 durante cada comparación.
- Con el equipo configurado como Read & write, el propietario confirmó lista directa vacía y valor de equipo seleccionado (EV-141, EV-143). Como miembro, la secundaria ve entrada Add a task y checkboxes activos; menú de proyecto sin Eliminar; detalle de tarea muestra controles de organización/gestión, fechas, recordatorios, repetición y Eliminar (EV-144, EV-146–EV-147). No se ejecutaron acciones.
- Con el equipo configurado como Admin y la lista directa vacía, la secundaria ve igualmente alta/checkboxes activos; el menú incluye Eliminar; el detalle muestra el mismo grupo de controles de tarea observado con Read & write (EV-149–EV-152). No se confirmó/eliminó/guardó ninguna acción.
- El propietario retiró la concesión temporal de equipo, restauró la concesión directa Read & write y la sesión secundaria volvió a abrir el proyecto. Estado final: secundaria miembro del equipo original; proyecto 7 compartido directamente con ella Read & write, no compartido con el equipo (EV-153–EV-162).
- DQ-21 quedó DONE. `roles.md`, cobertura, árbol, US-32, actividad sintética, navegación, observaciones técnicas e índice se actualizaron. No se avanzó a análisis/especificación y Chrome sigue abierto.
