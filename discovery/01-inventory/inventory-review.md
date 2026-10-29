# Auditoría inicial del inventario — 2026-10-29

**Alcance:** revisión documental de `discovery/01-inventory/` tras el primer recorrido. No se accedió a Vikunja ni se repitió la exploración. Este dictamen evalúa la cobertura que puede justificarse con EV-01..EV-07 y los registros existentes; no valida el comportamiento de la aplicación.

## Veredicto

**Cobertura conocida: parcial; inventario abierto.** Hay 22 funcionalidades candidatas distribuidas en cinco módulos, 18 historias candidatas y siete referencias de evidencia. La documentación identifica las áreas principales visibles para la cuenta autenticada, pero solo confirma una operación de alta: el equipo sintético (EV-05, EV-06). Las demás acciones de creación, edición, filtrado, cambio de estado, permisos y ajustes se conocen principalmente por controles o enlaces. No existe base para declarar saturación de áreas ni cobertura de otro rol.

La calidad es **suficiente como inventario exploratorio, insuficiente como inventario validado**. La estructura e IDs permiten continuar, pero la evidencia conservada es resumida: `evidences/README.md` cita snapshots ubicados en `.playwright-mcp`, fuera del directorio de evidencias exigido por `AGENTS.md`. No se preservó allí una copia de los snapshots ni capturas. EV-05 carece de nombre exacto de snapshot. Las descripciones EV permiten rastrear las observaciones a una sesión, URL y hora aproximada; no permiten verificar de forma autónoma cada control cuando desaparezcan los archivos temporales.

## Consistencia y correcciones aplicadas

| Hallazgo | Causa documental | Resolución |
|---|---|---|
| `roles.md` negaba la creación del equipo, mientras EV-05/06 y el registro confirman alta y rol `Admin` de la cuenta activa. | El documento de roles quedó anterior al recorrido de equipos. | Se registró el rol observado y se dejó como UNKNOWN el contexto de otro miembro. |
| FUN-16 decía que el menú de cuenta no se había inspeccionado; EV-07 y el registro indican apertura y visita a Ajustes Generales. | Actualización parcial del árbol. | Se corrigió FUN-16 y se añadió EV-07. |
| DQ-11 y DQ-14 seguían en TODO después del recorrido de cuenta; DQ-15 repetía DQ-09/10/12. | Backlog sin sincronizar y entrada agregada redundante. | DQ-11 quedó IN_PROGRESS, DQ-14 DONE y DQ-15 NOT_APPLICABLE; se conservaron todos los IDs. |
| `technical-discovery.md` solo mencionaba EV-01..EV-05 y omitía rutas visitadas de equipo y ajustes. | Registro técnico anterior a EV-06/07. | Se actualizaron las referencias y rutas documentadas, sin afirmar tecnología de implementación no comprobada. |
| `navigation-map.md` cerraba la observación a las 08:42 y formulaba `/about` y `/user/settings/*` como destinos visitados. | Mezcla de enlaces visibles con páginas abiertas. | Se amplió la hora a 08:43 y se distinguieron destinos enlazados de visitas efectivas. |
| FUN-02, FUN-11, FUN-12 y US-02 podían leerse como cambios de estado, edición o incorporación ejecutados. | Los controles visibles se expresaban como resultado probado. | Se explicitó que esas operaciones no constan ejecutadas. FUN-06 quedó marcado INFERRED; FUN-07 separa consulta visible de gestión pendiente. |
| US-14 solapaba US-15, US-16 y US-18. | Una historia general absorbía las preferencias de historias más específicas. | Se acotó US-14 a nombre y proyecto predeterminado, conservando su ID. |

## Problemas y límites que permanecen

- **Trazabilidad de operaciones:** EV-01 respalda controles de tarea, no una creación ni un cambio de estado; EV-03 respalda botones de filtros y bucket, no su resultado; EV-04 respalda el formulario de etiqueta, no su persistencia. EV-07 respalda opciones visibles, no guardado de preferencias, gestión de seguridad ni uso de integraciones. Las US-01/02/05/06/07/15/16/18 son candidatas, no comportamientos validados.
- **Coherencia entre funcionalidades e historias:** FUN-04, FUN-06, FUN-07 y FUN-13 no tienen historia propia. Esto no constituye por sí solo un defecto: FUN-13 es navegación transversal; FUN-04 y FUN-07 necesitan inspección; FUN-06 sigue inferida. US-04 y US-11 describen acceso/navegación, y US-09 describe abrir un control cuyo contenido se desconoce. Antes de especificar, el explorador debería determinar si aportan capacidades autónomas o son puntos de entrada de otras funciones. FUN-18/20/21/22 se superponen como área de ajustes; la acotación de US-14 reduce la duplicidad, pero la agrupación final depende del recorrido pendiente.
- **Permisos y estados:** solo se observó la cuenta `rea_discovery_20261028b`, incluida su condición `Admin` en el equipo que creó. No se infieren permisos de propietario de proyecto, invitado, miembro ni segundo administrador a partir de menús visibles. Próximas se vio vacía; tampoco hay observación de notificaciones, búsqueda ni filtros abiertos.
- **Áreas de navegación sin cobertura de pantalla:** el detalle `/tasks/3`, los filtros guardados, vistas alternativas de proyecto, el contenido de las secciones de cuenta y `/about` aparecen como enlaces o destinos, sin recorrido documentado. La navegación a `/user/settings/general` sí está observada; la presencia de otros enlaces de ajustes no prueba acceso funcional a sus páginas.
- **Conservación de evidencia:** el índice de EV está dentro de `evidences/`, pero el material primario permanece en `.playwright-mcp`. El próximo incremento debería incorporar los snapshots relevantes al directorio de evidencias y precisar el archivo correspondiente a EV-05; no debe reconstruir evidencias que ya no estén disponibles.

## Exploraciones recomendadas a `functional_explorer`

Ordenadas por **valor esperado de información nueva**. Cada acción se limita a identificar superficies y capacidades de inventario, sin derivar reglas de negocio ni criterios de aceptación.

| Prioridad | Referencias | Causa de cobertura parcial o faltante | Acción y objetivo concreto |
|---|---|---|---|
| 1 | DQ-02, FUN-04, EV-01 | El detalle de tarea solo figura como enlace; bloquea el inventario de acciones sobre la entidad central. | Abrir `/tasks/3` desde el enlace observado, registrar pestañas, menús y acciones visibles, con URL y evidencia persistida. |
| 2 | DQ-04, FUN-05/06, EV-01/03 | El acceso Proyectos y un tablero se conocen, pero el alta, las vistas y opciones contextuales no; FUN-06 sigue inferida. | Recorrer lista, controles de alta, menú contextual y selector de vistas de un proyecto existente; confirmar o descartar las capacidades candidatas sin guardar cambios innecesarios. |
| 3 | DQ-05/06, FUN-07/08/09, EV-01/03 | Filtros guardados, Filtros y Create a bucket se registraron como puntos de entrada sin abrir. | Inspeccionar panel de filtros, filtro guardado y controles de bucket; si se necesita estado poblado, usar datos sintéticos autorizados y registrar qué acción produjo cada pantalla. |
| 4 | DQ-01/03, FUN-01/03, EV-01/02 | Alta rápida y Próximas solo muestran controles o estado vacío; el contenido dependiente de fecha no se observó. | Abrir ayuda de prefijos; identificar controles del intervalo de Próximas y, con una tarea sintética fechada si hace falta, documentar la vista poblada. |
| 5 | DQ-07, FUN-10, EV-04 | Se abrió el formulario de etiqueta, pero no hay evidencia de persistencia ni de acciones posteriores. | Completar el alta sintética, volver al listado y observar menú y posible asociación con tarea, sin convertir el resultado en reglas de negocio. |
| 6 | DQ-09/10/12, FUN-14/15/17, EV-01 | Tres controles globales siguen sin abrir; DQ-15 era una duplicidad del backlog. | Abrir búsqueda/acción rápida, notificaciones y atajos; registrar contenido, estados vacíos y destinos visibles por separado. |
| 7 | DQ-08/11/16, FUN-11/12/19, EV-06/07 | La edición de equipo y numerosas secciones de cuenta se conocen solo por controles o enlaces. | Completar el inventario de pantallas informativas y acciones visibles, sin guardar ajustes sensibles, emitir tokens, invitar usuarios ni eliminar recursos. |
| Condicionada | DQ-13, roles.md | No hay cuenta secundaria ni constancia de autorización para alta o acceso con otro rol; es un bloqueo de contexto, no un fallo de navegación. | Si el operador aporta una segunda cuenta autorizada, registrar vistas y controles de miembro/invitado y comparar la visibilidad por rol. Mantener UNKNOWN hasta entonces. |

La referencia caducada que afectó al primer clic en el diálogo de equipo se resolvió durante la exploración y **no es un bloqueo vigente**. La ausencia de datos para estados poblados y la falta de segunda cuenta explican coberturas parciales distintas: la primera puede tratarse con datos sintéticos; la segunda depende de autorización externa.

## Criterio para el siguiente incremento

Actualizar IDs existentes con nuevas EV y estados de cobertura solo cuando el explorador aporte observaciones nuevas. Mantener separadas las etiquetas **OBSERVED**, **INFERRED** y **UNKNOWN**; reservar **VALIDATED** para una comprobación específica posterior. Esta auditoría no inicia análisis funcional ni especificación.

## Revisión incremental 1 — 2026-10-29

**Alcance:** contraste documental exclusivo del incremento EV-08..EV-44 y su relación con el dictamen inicial. Se mantuvo el veredicto histórico anterior como línea de base. El inventario pasa a 23 FUN y 25 US candidatas. El recorrido nuevo amplía claramente tareas, proyectos, filtros, etiquetas, Próximas y controles globales; **la superficie conocida accesible aún no puede declararse completa**.

### Dictamen de evidencia y consistencia

| Hallazgo del incremento | Evaluación y corrección |
|---|---|
| EV-36 contiene un combobox de prioridad con opciones Sin definir, Baja, Media, Alta, Urgente y HACER AHORA. | Contradice la afirmación de que el panel de prioridad no abrió. Se corrigieron FUN-04, DQ-02, `coverage.md` y el índice de EV. Las demás acciones de tarea siguen sin panel documentado. |
| EV-37, EV-38, EV-39, EV-43 y EV-44 tienen únicamente «Vikunja está cargando…». | Su existencia como archivo no prueba el contenido atribuido. Se corrigieron las afirmaciones verificables sobre Avatar e importación en FUN-19/23, US-25, cobertura, mapa e índice. El registro conserva lo declarado por el explorador, separado de lo acreditado por los snapshots. EV-39 tampoco acredita Kanban poblado; EV-40 sí. |
| EV-15 se llama `kanban-bucket-created.yml`, pero muestra el título en un campo activo y un indicador de carga, sin bucket nuevo confirmado. EV-41 muestra de nuevo el campo abierto. | Se conserva el ID y el archivo; el nombre no constituye evidencia de creación. DQ-05 permanece parcial. Dos intentos de Enter con el mismo mecanismo no prueban que la función sea inaccesible o defectuosa. |
| FUN-01 atribuía a la entrada de Resumen un alta ejecutada desde un proyecto; FUN-06 citaba EV-21/24, que corresponden a filtro guardado; US-22 repetía el alta de US-07. | Se separaron contexto observado y acción ejecutada, se corrigió la trazabilidad de FUN-06 y se acotó US-22 a asociar una etiqueta existente. Todos los IDs permanecen. |
| DQ-15 seguía diciendo que DQ-09/10/12 estaban pendientes, pese a EV-32..34. | Se sincronizó el resultado del backlog. |

**Calidad del incremento:** buena ampliación de cobertura y varias operaciones sintéticas trazadas (proyecto, filtro, etiqueta, tarea y fecha). Persisten una brecha de evidencia primaria en cinco EV, acciones visibles aún sin abrir y una deducción indebida de bloqueo para pantallas informativas. EV-01..04/07 siguen referidas a snapshots fuera de `evidences/`. El estado `DONE` de un DQ significa que se identificó su superficie prevista, no que exista especificación completa ni que cada operación fue validada.

### Evaluación de parciales y bloqueos

| DQ | Estado de auditoría | Causa demostrada, límite y siguiente objetivo |
|---|---|---|
| DQ-02, IN_PROGRESS | **Justificado como parcial; bloqueo general no demostrado.** EV-08 y EV-35 muestran el detalle y sus acciones; EV-27..29 acreditan etiqueta/fecha, y EV-36 abre prioridad. El registro dice que reintentos posteriores de `/tasks/3` y `/tasks/5` quedaron en carga, pero los snapshots conservados no aíslan la causa. Objetivo: documentar al menos los paneles secundarios aún accesibles desde una carga estable y guardar evidencia de cualquier espera persistente con su contexto. |
| DQ-05, IN_PROGRESS | **Justificado como parcial, no como función imposible.** EV-14/15 y EV-40/41 muestran el campo de bucket y su permanencia tras Enter; no hay confirmación ni nuevo bucket. El mismo modo de confirmación se repitió dos veces, sin probar otro gesto visible. Objetivo: identificar si hay confirmación al perder foco o por otro control de UI y, si no aparece, registrar el estado final sin atribuir defecto. El menú de bucket ya aportó información nueva. |
| DQ-13, BLOCKED | **Justificado.** Solo existe sesión autorizada de la cuenta actual; no consta otra cuenta ni autorización para crearla. EV-05/06 acredita Admin del equipo propio, no permisos de otro rol. Objetivo condicionado: cuando el operador facilite una segunda cuenta autorizada, comparar únicamente superficies de miembro/invitado. Mientras tanto, mantener roles alternativos UNKNOWN. |
| DQ-16, antes BLOCKED | **Bloqueo total no justificado.** Leer encabezados, controles vacíos y opciones informativas no equivale a emitir tokens, exportar, importar, guardar ni eliminar. Ya se declaró navegación a importación; sus EV-43/44 quedaron en carga. Se cambió a IN_PROGRESS. Objetivo: recorrer pantallas informativas de seguridad, datos e integraciones con evidencia legible y detenerse antes de revelar secretos o ejecutar cambios. Si una página concreta exige una acción sensible para mostrar su contenido, bloquear solo esa acción y registrar la dependencia. |

### Siguiente trabajo para `functional_explorer`, por valor esperado

| Prioridad | Causa | Objetivo de inventario |
|---|---|---|
| 1 | EV-38/43/44 no contienen contenido de Avatar ni importación y DQ-16 quedó prematuramente bloqueado. | Reabrir las pantallas informativas, esperar contenido y conservar snapshots legibles con URL, rol y hora. Hacer lo mismo con las secciones de cuenta accesibles sin efectos; no seleccionar archivos ni accionar operaciones sensibles. |
| 2 | DQ-02 sigue parcial, aunque prioridad sí está documentada. | Reabrir la tarea propia desde una vista estable e inspeccionar uno a uno progreso, asignación, relaciones, movimiento, adjuntos y recordatorios, registrando solo controles y destinos; si la carga impide continuar, conservar evidencia del estado y contexto. |
| 3 | DQ-05 no confirmó bucket y EV-15 tiene nombre engañoso. | Examinar la confirmación visible tras escribir el nombre, incluido perder el foco si la interfaz lo permite; documentar si aparece bucket nuevo después de volver al tablero. No inferir éxito por el nombre del archivo. |
| 4 | El menú contextual de proyecto se ve en snapshots, pero la configuración del proyecto propio no está inventariada; la creación desde Resumen y el cambio de estado de tarea solo son controles visibles. | Abrir el menú contextual del proyecto propio y registrar destinos; comprobar los puntos de entrada de tarea desde Resumen y estado sin exceder la fase de inventario ni tocar datos ajenos. |
| 5 | La búsqueda no devolvió la tarea por texto exacto y notificaciones permanece vacía, sin que eso pruebe ausencia de funciones. | Registrar los modos/sugerencias de búsqueda con una entrada propia y dejar explícito el estado vacío de notificaciones; usar otro escenario solo si aporta una superficie nueva de inventario. |

Las prioridades 1–4 corresponden a **huecos todavía accesibles o pendientes de evidencia**. El único bloqueo de contexto plenamente acreditado es DQ-13; las acciones sensibles dentro de DQ-16 están fuera del alcance operativo, pero la navegación informativa puede continuar. Esta revisión no avanza a análisis ni especificación.

## Revisión incremental 2 — 2026-10-29

**Alcance:** examen documental del incremento EV-45..EV-72, sus referencias y los estados actualizados. No se navegó ni se consultó código o fuentes externas. Las capturas cargadas EV-45..49 reparan la brecha de Avatar e importación de la revisión anterior; EV-54..60 muestran el detalle de tarea cargado; EV-61 documenta la pérdida de foco del bucket. Se distinguen las capacidades **identificadas** de operaciones que permanecen sin ejecutar.

### Veredicto independiente

**La afirmación «no quedan TODO/IN_PROGRESS accesibles» no es correcta. La superficie conocida accesible sigue incompleta.** La mayoría de las áreas principales está identificada, pero EV-57/59 deja visible un selector de tipo de relación sin opciones documentadas, EV-60 muestra «Add a reminder…» sin abrir, EV-51 enlaza Webhooks de proyecto, EV-69 muestra ayuda de enlaces compartidos, y el menú de ajustes enumera varias páginas no visitadas. Estos huecos son accesibles con la cuenta actual y pueden revisarse hasta el contenido informativo sin alterar datos. DQ-13 sigue siendo el único bloqueo de rol acreditado: falta una segunda cuenta autorizada.

La calidad de trazabilidad del incremento **mejoró**: hay YAML y PNG de pantallas cargadas, rutas, controles y actividades sintéticas. El veredicto de completitud se limita a la superficie observada para la cuenta actual; no se extrapola a otro rol ni a estados que exijan datos o acciones sensibles. EV-01..04/07 siguen fuera de `evidences/`, y EV-37/38/39/43/44 siguen siendo capturas transitorias no aptas para acreditar contenido.

### Hallazgos y correcciones

| Hallazgo | Causa y resolución documental |
|---|---|
| DQ-16 se cerró como DONE pese a enlaces visibles a email, CalDAV, MCP, Atom Feed, tokens API, sesiones, webhooks, bots y eliminación sin pantalla acreditada. | Se confundió el riesgo de ejecutar operaciones con el acceso de lectura a sus formularios. Se devolvió DQ-16 a IN_PROGRESS y se corrigió `coverage.md`. Solo una puerta que exija credencial o una acción con efectos justifica detener esa rama. |
| DQ-02 se cerró con la expresión «tipos de relación inspeccionados», pero EV-57/59 solo muestra el selector cerrado; EV-60 muestra el botón de añadir recordatorio. | Los controles están identificados, sus opciones siguen desconocidas. Se corrigieron FUN-04, backlog y cobertura; DQ-02 vuelve a IN_PROGRESS para abrir esos controles sin aplicar cambios. |
| El menú de proyecto EV-51 contiene enlace Webhooks y la pantalla Compartir EV-69 contiene ayuda de enlaces compartidos, sin contenido posterior documentado. | Se añadió DQ-17 TODO para el recorrido informativo de esos destinos, conservando todos los IDs previos. Los controles de crear enlace, duplicar, archivar y eliminar no se ejecutaron ni se presumen seguros. |
| US-20 citaba EV-24, que corresponde al filtro guardado, y el registro sintético de bucket omitía el intento por pérdida de foco. | Se corrigieron las referencias de US-20 y la secuencia de la actividad sintética. |

DQ-05 puede considerarse **DONE para el inventario de controles visibles**: EV-14/15, EV-40/41 y EV-61 muestran campo de alta, dos intentos por Enter, pérdida de foco y retorno a los tres buckets originales. El resultado de alta permanece **UNKNOWN**; esas observaciones no prueban ni creación ni defecto general. No se requiere forzar la persistencia durante inventario. La búsqueda exacta de tarea y la asignación a la propia cuenta tampoco produjeron resultado concluyente; se mantienen como límites de escenario, no como ausencia de función.

### Última revisión recomendada a `functional_explorer`

| Prioridad | Causa del hueco | Acción concreta y objetivo |
|---|---|---|
| 1 — DQ-16 | Nueve destinos de ajustes se conocen por enlaces, pero carecen de pantalla y EV propia. | Abrir uno a uno email, CalDAV, MCP, Atom Feed, tokens API, sesiones, webhooks, bots y eliminación; registrar solo encabezado, secciones y controles visibles con URL/rol/hora. No revelar valores secretos, introducir credenciales, emitir tokens, exportar, guardar ni eliminar. Si una página exige credencial antes de mostrar contenido, anotar esa puerta y pasar a la siguiente. |
| 2 — DQ-02 | Los tipos de relación y opciones de recordatorio siguen ocultos detrás de controles ya visibles. | Abrir el selector de tipo y «Add a reminder…» sobre la tarea propia; registrar opciones y estados iniciales sin crear relación ni recordatorio. Si alguno produce inmediatamente un cambio, detener ese flujo y dejar el resultado UNKNOWN. |
| 3 — DQ-17 | Webhooks de proyecto y ayuda de enlace compartido son destinos visibles aún sin descripción. | Abrir Webhooks del proyecto propio y la ayuda de Compartir; registrar contenidos informativos. No crear endpoint, integración ni enlace público. |

Con esos recorridos, el auditor podrá reevaluar la **superficie conocida accesible**. DQ-13 y cualquier rama que realmente requiera otra cuenta o una acción sensible deben permanecer separadas del cierre de la cuenta actual. Esta revisión no inicia análisis ni especificación.

## Revisión incremental 3 y veredicto final — 2026-10-29

**Alcance:** revisión documental de EV-73..EV-85 y del cierre de DQ-02/16/17. No se accedió a Vikunja, al navegador ni a código. Este es el tercer y último ciclo de auditoría del encargo.

### Veredicto

**El inventario de las superficies funcionales principales visibles para la cuenta actual queda cubierto a nivel de Fase 1. No puede certificarse como completo en sentido absoluto ni como comportamiento validado.** DQ-02/16/17 tienen ahora evidencia del contenido que faltaba; el backlog no conserva tareas `TODO` o `IN_PROGRESS`, y DQ-13 sigue `BLOCKED` por ausencia de una segunda cuenta autorizada. El estado `PARTIAL_BLOCKED` de la cobertura es coherente con ese límite de rol y con las operaciones que deliberadamente no se ejecutaron.

La decisión de cierre se refiere a **identificar capacidades y puntos de entrada**, no a confirmar todas sus operaciones. Se conserva `UNKNOWN` para la persistencia de un bucket, resultados de búsqueda/asignación no concluyentes, acciones sensibles, uso efectivo de webhooks y enlaces públicos, y vistas de otros roles. Los documentos de la aplicación enlazados desde CalDAV, MCP, tokens API y webhooks no se visitaron; EV-74/75/77/79 solo registra sus enlaces y, en los resúmenes, no permite determinar si son páginas internas o documentación externa. Por ello no se afirma haber recorrido literalmente cada destino visible.

### Exactitud, trazabilidad y cierre del backlog

| Comprobación | Dictamen documental |
|---|---|
| DQ-02 / EV-82..83 | EV-82 muestra diez tipos concretos de relación en el selector de la tarea propia. EV-83 muestra los presets de recordatorio y las entradas Personalizado/Fecha y hora. FUN-04 y US-19 mantienen la distinción entre opciones visibles y relación/recordatorio creados. Cierre `DONE` justificado para inventario. |
| DQ-16 / EV-73..81 | Las nueve secciones pendientes tienen URL, cuenta, hora UTC y resumen de controles. Sus archivos son resúmenes DOM depurados, no capturas completas; son suficientes para identificar la pantalla sin atribuir resultados de guardado. TOTP y eliminación exigen contraseña para continuar; tokens, sesiones, webhooks y bots no se alteraron. Cierre `DONE` justificado para lectura informativa. |
| DQ-17 / EV-84..85 | EV-84 documenta el formulario de Webhooks del proyecto y sus controles; EV-85 documenta la ayuda de enlace compartido. FUN-24/25 y US-26/27 son candidatas; no acreditan entrega de webhook ni acceso real por enlace. Cierre `DONE` justificado para superficie visible. |
| DQ-05 / EV-14..15, EV-40..41, EV-61 | El punto de alta de bucket está identificado; Enter y pérdida de foco no confirmaron creación. Se ajustó la acción del backlog para reflejar identificación e intento, conservando DQ-05 y `DONE` de inventario. El resultado de creación queda `UNKNOWN`; no se infiere defecto general. |
| IDs y referencias | El árbol conserva 25 FUN, las historias 27 US y el backlog 17 DQ con IDs estables. EV-73..85 existen en `evidences/` y tienen entrada de índice; no se reutilizó ningún ID. Se corrigieron la hora final del mapa (EV-85 llega a 09:39 UTC) y la formulación de sesiones: EV-78 informa de revocación, pero su resumen no muestra un botón de revocación en la sesión actual. |

La evidencia EV-79 incluye dos textos de interfaz potencialmente tensos: la introducción dice que las notificaciones webhook abarcan todos los proyectos y la ayuda del selector de eventos menciona el proyecto actual. En inventario solo se registra esa coexistencia; el alcance efectivo queda **UNKNOWN** y no se convierte en regla de negocio. EV-01..04/07 siguen referidas a snapshots fuera de `evidences/`; EV-37/38/39/43/44 solo conservan carga. Esos límites de conservación reducen verificabilidad de la primera ronda, aunque los incrementos posteriores sustituyen gran parte del contenido funcional.

**Conclusión operativa:** el inventario es apto como catálogo inicial, trazable y revisable de la cuenta observada. No declara cobertura de otros roles, saturación de estados ni equivalencia funcional demostrada. No se propone un cuarto ciclo de auditoría en este encargo y no se avanza a análisis ni especificación.

## Auditoría incremental de cuentas y permisos — 2026-10-29

Esta revisión fue autorizada por el operador después del cierre anterior. Los dictámenes previos permanecen como historia; **el veredicto vigente es el de esta sección**. Se revisaron exclusivamente documentos y EV-86..EV-108, sin acceder a la aplicación ni usar navegador. La versión actual de `AGENTS.md` autoriza crear cuentas sintéticas y configurar permisos sobre recursos propios; el prompt vigente exige contrastar los roles realmente observados. En consecuencia, la antigua ausencia de segunda cuenta ya no es un bloqueo.

### Veredicto vigente

**La cobertura de colaboración es parcial y hay trabajo accesible pendiente.** DQ-13 está correctamente `DONE` para el registro de la segunda cuenta y la comparación de permisos **directos de usuario** Read only, Read & write y Admin en un proyecto propio, además de miembro/Admin en el equipo sintético. Ningún DQ permanece `BLOCKED`. El estado `PARTIAL_BLOCKED` no describía esa situación: se cambió a `PARTIAL_IN_PROGRESS` en cobertura y árbol, con DQ-18..20 para las lagunas concretas. La ausencia de bloqueo tampoco convierte el inventario en completo.

El incremento aporta evidencia sólida de diferencias visibles: EV-90/92 muestra tarea accesible con controles deshabilitados en Read only; EV-94..97 muestra alta habilitada y una tarea creada con Read & write; EV-98/99 abre menú y edición con Admin; EV-93/104 muestra la vista de miembro de equipo sin edición; EV-100/101 muestra controles de Admin de equipo. EV-102/105/106 confirma la asignación de una tarea entre cuentas, y EV-108 muestra dos avisos no leídos con controles de gestión. Son observaciones de **estas cuentas y recursos**, no reglas universales de autorización.

### Matriz de cobertura auditada

| Cuenta y contexto | Rol/permiso configurado o visible | Evidencia de capacidad | Límite de la evidencia |
|---|---|---|---|
| Primaria, recursos sintéticos propios | Admin visible de equipo; creadora del proyecto | Alta/gestión de equipo, compartir proyecto y asignar tarea: EV-05/06, EV-87/88, EV-102/105 | No se probó rol global ni se ejecutaron acciones destructivas. |
| Secundaria, antes de participar | Cuenta autenticada; sin rol global visible | Resumen y navegación propia sin recursos primarios: EV-86 | La ausencia del enlace **no demuestra denegación por URL directa**. DQ-20. |
| Secundaria, equipo sintético | Miembro | Lista de miembros y «Abandonar equipo», sin formulario de edición en esa vista: EV-93/104 | Acceso al proyecto por pertenencia al equipo no probado. DQ-18. |
| Secundaria, equipo sintético | Admin temporal | Edición/alta de miembros y controles de rol/remoción visibles: EV-100/101 | La capacidad de guardar o eliminar no fue probada; el rol se restauró. |
| Secundaria, proyecto compartido directamente | Read only | Proyecto/tarea visibles, checkbox deshabilitado, sin alta ni menú de configuración: EV-88..92 | No se ensayó acceso indirecto por equipo. |
| Secundaria, proyecto compartido directamente | Read & write según registro; estado final declarado | Alta y checkbox habilitados; tarea nueva; asignación propia y notificaciones: EV-94..97, EV-106..108 | El botón de menú de proyecto se ve, pero sus opciones no se abrieron. El selector final de permiso no está capturado desde la cuenta primaria. DQ-19. |
| Secundaria, proyecto compartido directamente | Admin temporal | Menú de proyecto y formulario de edición visibles: EV-98/99 | No se guardó edición; el permiso se restauró según el registro. |

### Consistencia, trazabilidad y datos sensibles

- Se conservaron todos los IDs existentes. Se añadió FUN-27/US-31 para `/register`, que figuraba en EV-103, el log y la actividad sintética sin representación funcional. US-30 se vinculó a FUN-04 (consulta de tarea asignada), en vez de FUN-26 (compartición de proyecto). El árbol tiene ahora 27 FUN, las historias 31 US y el backlog 20 DQ.
- `roles.md` separa el permiso directo observado de una eventual compartición por equipo. También distingue «recurso ausente en navegación» de «acceso denegado». EV-94/107 presenta botón de menú con Read & write, mientras EV-98 documenta sus opciones con Admin: no se puede afirmar que solo Admin vea un menú. El valor final Read & write consta en el registro del explorador, pero los snapshots posteriores de la secundaria acreditan controles compatibles, no el selector de permiso final de la primaria.
- Se corrigió la cabecera de `synthetic-data-activity.md`, que solo citaba la cuenta primaria, y una nota que decía que no se había abierto el menú contextual pese a EV-98. El índice EV ahora distingue ambas sesiones; `technical-discovery.md` incluye `/register` y `/tasks/6` y reconoce las dos cuentas.
- En los archivos textuales EV-86..108 revisados no se encontró un valor de contraseña, token o correo real. EV-103 contiene un **correo de ejemplo como placeholder**, no una credencial. Los nombres de usuario sintéticos se conservan para trazabilidad. No se inspeccionaron recursos ajenos ni se presume permiso global.
- No se detecta duplicidad sustancial nueva en US-28/29/30: describen concesión de permiso, creación en proyecto compartido y consulta de tarea asignada, respectivamente. Permanecen historias candidatas; los efectos de editar, eliminar, revocar o marcar notificaciones leídas no se consideran validados.

### Lagunas accesibles y acciones para `functional_explorer`

| Prioridad | Causa comprobada | Preparación, sesión y objetivo |
|---|---|---|
| 1 — DQ-18 | La UI de Compartir muestra «Compartido con estos equipos» (EV-69/88), pero solo se configuró permiso **directo a usuario**. La secundaria tiene Read & write directo, que ocultaría el efecto de pertenecer al equipo. | En la cuenta primaria, compartir el proyecto sintético con el equipo sintético mediante UI. Aislar el permiso de equipo retirando temporalmente la concesión directa a la secundaria sobre ese recurso propio, o usar otro recurso sintético sin concesión directa. Entrar como secundaria miembro, registrar qué proyecto/tarea/controles aparecen y qué permisos muestra realmente el selector de equipo. Restaurar el estado de prueba y conservar evidencias de la configuración. |
| 2 — DQ-19 | EV-94/107 muestra el botón del menú de proyecto bajo Read & write; solo EV-98 abre sus opciones bajo Admin. El permiso final consta en el log, sin captura del selector. | Entrar como secundaria con Read & write directo, abrir el menú del proyecto propio y registrar opciones visibles sin ejecutarlas. Desde la primaria, abrir Compartir y conservar el selector final Read & write de esa cuenta. Objetivo: comparación atribuible al permiso configurado. |
| 3 — DQ-20 | EV-86 acredita que no aparecían los recursos primarios en la navegación inicial, pero no el resultado de una URL conocida. | Con la primaria, preparar un proyecto y, si aporta cobertura nueva, un equipo sintéticos **sin compartir**. Con la secundaria en sesión aislada, abrir sus URLs previamente observadas y registrar solo la respuesta de UI. Objetivo: distinguir ausencia en navegación de acceso efectivo; no inferir una regla de seguridad de una sola pantalla. |

DQ-13 no vuelve a `BLOCKED`: su objetivo directo se cumplió. Tampoco se usa `BLOCKED` para acciones sensibles deliberadamente fuera de la fase de inventario. El resultado de alta de bucket, efectos de cambios destructivos y roles globales no visibles siguen como límites, sin desplazar las tres lagunas accesibles anteriores. No se avanza a análisis ni especificación.

## Segunda auditoría incremental de cuentas y permisos — 2026-10-29

**Alcance:** revisión exclusivamente documental de EV-109..EV-134, DQ-18..DQ-20 y su consistencia con los documentos actuales. No se accedió a Vikunja ni al navegador. Las secciones anteriores conservan los dictámenes de su momento; **este es el veredicto vigente**.

### Veredicto vigente y trazabilidad

**DQ-18, DQ-19 y DQ-20 están justificadamente DONE, pero la superficie conocida accesible de colaboración sigue parcial.** EV-117 muestra que el selector de permiso para equipo permite Read only, Read & write y Admin. Solo se configuró Read only y se observó la sesión secundaria en ese contexto. Los otros dos permisos son accesibles con la cuenta, equipo y proyecto sintéticos ya preparados, sin impedimento documentado. Por ello se añadió DQ-21 TODO y se corrigió `coverage.md`/`functional-tree.md` a `PARTIAL_IN_PROGRESS`. No hay DQ `BLOCKED`. La ausencia de otros TODO no habría acreditado completitud; el hueco procede del selector observado.

| Contexto | Evidencia y resultado sustentado | Límite |
|---|---|---|
| Concesión directa Read & write a secundaria | EV-109 muestra permiso seleccionado y lista de equipos vacía; EV-110 abre el menú con Editar, Views, Background settings, Compartir, Duplicar, Archivar, Suscribirse, Webhooks y Crear proyecto, sin Eliminar. EV-98 había mostrado Eliminar bajo Admin directo. | Comparación de opciones visibles en ese recurso; no prueba autorización efectiva de cada operación. |
| Secundaria miembro; solo equipo Read only | EV-111/112 retira la concesión directa; EV-117 muestra equipo Read only y lista directa vacía; EV-118/119 documenta proyecto y tareas visibles con controles de edición deshabilitados. | Read & write/Admin de **equipo** aparecen en EV-117, pero no fueron configurados ni observados desde secundaria. DQ-21. |
| Secundaria sin participación en recursos de control | EV-120..123 acredita alta de proyecto y equipo sin compartir/añadir a secundaria. EV-124/125 muestra aviso UI «You don't have the permission to see this» al abrir sus URLs directas. | No se infiere estado HTTP ni regla universal. EV-125 también presenta un encabezado y tabla de miembros vacía; el aviso no significa ausencia literal de todo contenido. |
| Baseline posterior | EV-126/127 muestra retirada de la concesión temporal de equipo; EV-128..133 muestra nueva concesión directa, desde Read only inicial hasta Read & write seleccionado y sin equipo compartido; EV-134 muestra la secundaria de nuevo con controles de alta/estado. | El baseline documentado es secundaria miembro del equipo y permiso directo Read & write en proyecto 7; proyecto 7 sin compartir al equipo. |

La secuencia EV-109..134 tiene los 26 IDs esperados, todos con archivo de evidencia y metadatos de sesión, ruta y hora. No se hallaron líneas con valores de contraseña, token, secreto o correo en los YAML de este incremento mediante búsqueda textual; este control no sustituye inspección de contenidos no textuales. La advertencia de EV-127 menciona posible pérdida de asignaciones, suscripciones y webhooks de quien pierda acceso; se registra como **aviso visible**, sin atribuir efectos ejecutados. Se actualizó el índice de evidencias y se quitó una fila duplicada de `/register` en el mapa de navegación, sin alterar IDs.

### Acción priorizada para `functional_explorer`

| Prioridad | Causa | Acción y objetivo de Fase 1 |
|---|---|---|
| 1 — DQ-21 | Los valores Read & write y Admin para **equipo** son seleccionables en EV-117, pero solo existe observación de Read only por equipo. La concesión directa restaurada en el baseline enmascararía el origen del acceso. | En la cuenta primaria, retirar temporalmente la concesión directa del proyecto 7 o usar otro proyecto sintético sin concesión directa; compartirlo con el equipo sintético en Read & write. Entrar como secundaria **miembro** y registrar lista, tarea, controles de alta y menú. Repetir con permiso de equipo Admin, registrando solo diferencias visibles. Conservar selector configurado y hora/URL/rol en cada paso. Restaurar secundaria como miembro, permiso directo Read & write y ninguna compartición de proyecto 7 con equipo; dejar evidencia del baseline. |

No se requiere una prueba cartesiana de todos los permisos, acciones, recursos y estados para completar este **inventario de superficie**. Las operaciones sensibles/destructivas, persistencia de bucket, reglas generales de permisos y roles globales no visibles continúan UNKNOWN o fuera del alcance de la fase. Tampoco se inicia análisis ni especificación.

## Tercera y última auditoría incremental de cuentas y permisos — 2026-10-29

**Alcance:** revisión documental de EV-135..EV-162 y del cierre de DQ-21, contrastados con la matriz, la cobertura y el backlog. No se accedió a la aplicación ni al navegador. Los dictámenes anteriores quedan como registro histórico; **el veredicto vigente y final de este encargo es el siguiente**.

### Veredicto final

**`COMPLETE_KNOWN_SURFACE` está justificado para el inventario de Fase 1 de los roles y permisos conocidos, accesibles y autorizados.** DQ-21 cerró el único hueco accesible identificado en la revisión anterior: el equipo compartido en Read & write y Admin se configuró con la concesión directa retirada y se observó la sesión secundaria miembro en cada caso. Los tres niveles de permiso directo y los tres de permiso de equipo, así como miembro/Admin de equipo y el contexto sin participación, tienen evidencia diferenciada. No queda DQ `TODO`, `IN_PROGRESS` ni `BLOCKED`; ese dato concuerda con la evidencia, pero por sí solo no fundamentaría la completitud. No se identifica otro contexto de rol o permiso **visible y accesible** que haya quedado sin preparar.

| Cuenta, rol y recurso | Evidencia decisiva | Cobertura y límite |
|---|---|---|
| Primaria, propietaria del proyecto y Admin de equipo sintéticos | EV-05/06, EV-51..53, EV-135, EV-143, EV-149, EV-161 | Configura y restaura concesiones sobre recursos propios; no se observó rol global. |
| Secundaria, permiso **directo** Read only / Read & write / Admin de proyecto | EV-88..99, EV-109/110, EV-133/134 | Comparación de controles y menús visibles; EV-110 muestra menú Read & write sin Eliminar y EV-98 el Admin con Eliminar. No acredita ejecución de cada opción. |
| Secundaria, miembro / Admin temporal de equipo | EV-93, EV-100/101, EV-104 | Superficies de miembros y gestión de equipo comparadas; terminó como miembro. |
| Secundaria miembro, permiso **solo por equipo** Read only | EV-112, EV-117..119 | Lista y tarea en lectura, con controles de cambio deshabilitados; concesión directa ausente. |
| Secundaria miembro, permiso **solo por equipo** Read & write | EV-143, EV-144, EV-146..148 | EV-143/148 muestra equipo Read & write y usuarios directos vacíos. Alta/checkboxes habilitados; menú de proyecto sin Eliminar; detalle de tarea con controles de gestión, incluido Eliminar de tarea. No se accionaron. |
| Secundaria miembro, permiso **solo por equipo** Admin | EV-149/150..153 | EV-149/153 muestra equipo Admin y usuarios directos vacíos; alta/checkboxes habilitados; menú de proyecto incorpora Eliminar. EV-152 muestra controles de tarea. No se accionaron. |
| Secundaria sin participación en recursos de control | EV-120..125 | URLs directas de proyecto y equipo no compartidos muestran aviso UI de falta de permiso; EV-125 también contiene una sección de miembros vacía. No se infiere estado HTTP ni regla universal. |
| Baseline final | EV-155/156, EV-160..162 | Equipo retirado de la compartición del proyecto 7; secundaria miembro del equipo y con concesión **directa** Read & write en el proyecto, confirmada por selector y vista de secundaria. |

### Trazabilidad, consistencia y límites

EV-135..162 comprende los 28 IDs consecutivos esperados, con archivo, hora UTC, URL y cuenta/rol en el encabezado. EV-145 registra expresamente un menú de filtro abierto por error y no se usa para sustentar el menú del proyecto; este se acredita con EV-146. EV-149 muestra el selector Admin transitoriamente deshabilitado, y EV-153 confirma el estado Admin antes de retirarlo. FUN-26, US-32, `roles.md`, `coverage.md`, el índice de evidencias y DQ-21 conservan la distinción entre permiso configurado y controles observados. Los identificadores siguen únicos y consecutivos: 27 FUN, 32 US y 21 DQ. Una búsqueda textual de asignaciones explícitas de contraseña, token, secreto o correo en EV-135..162 no encontró valores; las cuentas sintéticas se identifican por nombre para trazabilidad.

El estado `COMPLETE_KNOWN_SURFACE` **no certifica** una matriz exhaustiva de autorización ni la ejecución exitosa de editar, eliminar, revocar o administrar cada objeto. La creación efectiva de bucket, el resultado de búsqueda exacta de tarea, las acciones sensibles de cuenta, los enlaces compartidos y los webhooks conservan límites `UNKNOWN` o de operación deliberadamente no realizada. La asignación de la tarea sintética a la segunda cuenta sí se observó en EV-102/105/106. No se observó ningún selector de rol global alternativo. EV-01..04/07 permanecen referidos a snapshots externos a `evidences/`, y EV-37/38/39/43/44 son capturas de carga: son límites de conservación histórica, sin invalidar la comparación de roles de este incremento.

**Cierre de este encargo:** inventario apto como catálogo inicial de superficies observables con sus límites explícitos. No hay hueco accesible significativo identificado en la documentación actual, no se propone un cuarto ciclo y no se avanza a análisis ni especificación.
