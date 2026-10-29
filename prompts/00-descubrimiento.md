# Fase 1 — Descubrimiento funcional exhaustivo mediante exploración activa

## 1. Misión

Actúa como analista funcional senior especializado en ingeniería inversa black-box de aplicaciones web.

Tu misión es identificar, explorar y catalogar el máximo número posible de capacidades funcionales accesibles de la aplicación objetivo.

Aplicación: Vikunja  
URL: http://localhost:3456

El objetivo es generar un inventario jerárquico:

**Aplicación → Módulos → Funcionalidades → Historias de usuario candidatas**

No debes generar código ni especificaciones funcionales o técnicas detalladas.

**El discovery no consiste en localizar pantallas y documentar lo que podría hacerse. Consiste en recorrer las capacidades realmente accesibles, preparar los contextos necesarios y registrar todo lo que el sistema permite hacer.**

## 2. Restricciones

Lee y cumple `common/restrictions.md`, relativo a este prompt.

Estas restricciones prevalecen sobre las instrucciones del presente documento.

Trabaja exclusivamente mediante el navegador con las cuentas de prueba existentes o creadas para este descubrimiento. El operador autoriza expresamente el alta de cuentas sintéticas y la configuración de roles y permisos sobre recursos sintéticos propios para explorar los contextos funcionales necesarios.

Puedes utilizar:

- Playwright MCP como herramienta principal de exploración.
- Chrome DevTools MCP únicamente cuando aporte evidencias complementarias relevantes.
- DOM, accesibilidad, capturas y comportamiento observable.
- Tráfico HTTP generado por operaciones legítimas del navegador.
- Respuestas estructuradas y metadatos de navegador, cuando ayuden a identificar capacidades.

No puedes:

- Consultar código fuente, scripts JavaScript, bundles o source maps.
- Consultar repositorios ni documentación externa.
- Acceder a contenedores, procesos, ficheros o bases de datos originales.
- Invocar directamente endpoints no utilizados por la aplicación.
- Enumerar rutas artificialmente.
- Eludir controles de acceso.
- Consultar información ajena a los usuarios de prueba.
- Generar código de implementación.

No guardes credenciales, tokens ni datos sensibles en evidencias.

## 3. Regla principal: exploración activa y no superficial

**No se considera explorada una funcionalidad por haber identificado su botón, formulario, enlace o punto de acceso.**

Cuando detectes una capacidad accesible:

1. Abre el elemento.
2. Inspecciona las acciones y opciones que ofrece.
3. Determina si necesita datos o un contexto específico.
4. Prepara ese contexto cuando esté autorizado.
5. Ejecuta una operación representativa cuando sea necesario para revelar capacidades adicionales.
6. Inspecciona el resultado.
7. Identifica las nuevas acciones habilitadas.
8. Registra las funcionalidades descubiertas.

Repite este procedimiento con las nuevas capacidades encontradas.

**No traslades al informe de cobertura operaciones que puedes ejecutar de forma segura dentro del entorno de prueba.**

Por ejemplo, si identificas un formulario para crear un filtro, debes crear un filtro sintético y comprobar qué opciones de gestión aparecen posteriormente.

No es necesario probar todas las validaciones ni analizar exhaustivamente el funcionamiento del filtro.

La finalidad es descubrir sus capacidades, no especificar sus reglas.

## 4. Clasificación de acciones

Antes de ejecutar una acción, clasifícala.

### READ_ONLY

Navegación, apertura de menús, consulta de datos, visualización de formularios o cambio de pestañas sin persistencia.

Ejecuta estas acciones libremente dentro del ámbito autorizado.

### SYNTHETIC_WRITE

Creación o modificación de datos sintéticos propios.

Ejemplos:

- Crear proyectos.
- Crear tareas.
- Crear etiquetas.
- Crear filtros.
- Crear equipos.
- Modificar propiedades de elementos sintéticos.
- Relacionar entidades sintéticas.
- Crear las cuentas de prueba necesarias mediante la interfaz de registro disponible.
- Asignar o cambiar roles y permisos de esas cuentas en proyectos y equipos sintéticos propios, mediante controles legítimos de la interfaz.

Ejecuta estas operaciones cuando permitan descubrir nuevas capacidades.

### CONTROLLED_DESTRUCTIVE

Operaciones de eliminación o sustitución irreversible sobre recursos sintéticos identificados y aislados.

Puedes ejecutarlas únicamente si las restricciones comunes lo autorizan expresamente, existe una necesidad de descubrimiento y se ha registrado el recurso afectado.

Si no están autorizadas, documenta la capacidad visible sin ejecutar su confirmación final.

### SENSITIVE_OR_EXTERNAL

Operaciones con efectos sobre información ajena, credenciales reales, servicios externos, configuración global sensible, pagos o envíos a terceros.

No las ejecutes sin autorización específica.

Si una acción puede revelar nuevas funcionalidades pero está bloqueada por estas restricciones, registra la dependencia y continúa con otras áreas.

## 5. Estrategia de trabajo

Organiza el descubrimiento en ciclos funcionales, no en un recorrido lineal de pantallas.

Cada ciclo se compone de:

1. Seleccionar un área funcional pendiente.
2. Identificar los contextos relevantes.
3. Preparar datos sintéticos.
4. Explorar las capacidades disponibles.
5. Identificar nuevas capacidades o dependencias.
6. Actualizar el inventario.
7. Revisar la cobertura del área.
8. Continuar hasta agotar las oportunidades de descubrimiento accesibles.

No cambies de módulo dejando capacidades accesibles sin explorar, salvo que exista una dependencia que haga más eficiente preparar datos conjuntamente.

## 6. Cola de descubrimiento obligatoria

Mantén un archivo:

`discovery/01-inventory/discovery-backlog.md`

Cada elemento de la cola debe representar una exploración concreta.

Registra:

- Identificador de tarea.
- Módulo o área.
- Contexto necesario.
- Acción de descubrimiento.
- Motivo por el que podría revelar nuevas capacidades.
- Dependencias.
- Estado.
- Evidencia.
- Resultado.

Estados permitidos:

- TODO
- IN_PROGRESS
- DONE
- BLOCKED
- NOT_APPLICABLE

Cuando descubras una nueva acción, contexto o dependencia relevante, incorpórala a la cola.

Las tareas deben ser ejecutables y concretas.

Ejemplo de tarea correcta:

"Crear un filtro sintético y abrir sus opciones de gestión".

Ejemplo de tarea incorrecta:

"Investigar filtros más adelante".

No marques una tarea como DONE únicamente por haber localizado su punto de entrada.

Debe haberse realizado la exploración prevista o documentado por qué no era aplicable.

## 7. Preparación de escenarios sintéticos

Antes de explorar exhaustivamente un módulo, identifica los escenarios mínimos necesarios.

No te limites a un único registro cuando eso impida descubrir capacidades.

Según la funcionalidad observada, considera:

- Listas vacías y pobladas.
- Uno y varios elementos.
- Entidades con relaciones.
- Registros con distintas propiedades.
- Elementos con fechas.
- Elementos asignados y no asignados.
- Entidades compartidas.
- Elementos pertenecientes a diferentes agrupaciones.
- Usuarios con diferentes relaciones sobre recursos sintéticos.
- Diferentes vistas y configuraciones.

Estos escenarios son ejemplos, no funcionalidades que debas presumir existentes.

Crea los datos mediante la interfaz, usando los mecanismos normales de la aplicación.

Reutiliza los mismos datos para distintos recorridos cuando sea posible.

Registra su creación y modificación en el archivo de actividad de datos de prueba del proyecto.

## 8. Exploración funcional por entidad

Para cada entidad o recurso descubierto, explora los contextos aplicables.

### A. Creación

- Abrir el formulario.
- Identificar sus capacidades configurables.
- Crear un registro sintético representativo.
- Identificar las acciones disponibles después de crearlo.

### B. Consulta

- Vista de listado.
- Vista de detalle.
- Menús asociados.
- Acciones contextuales.
- Opciones de visualización.

### C. Modificación

- Abrir las opciones de edición.
- Identificar propiedades modificables.
- Ejecutar cambios representativos sobre datos sintéticos.
- Observar si aparecen nuevas capacidades o estados.

### D. Organización

- Ordenación.
- Filtrado.
- Agrupación.
- Selección múltiple.
- Relaciones entre entidades.
- Vistas alternativas.

### E. Colaboración

- Compartición.
- Asignación.
- Invitación.
- Participación de varios usuarios.
- Roles visibles.
- Acciones disponibles en contextos compartidos.

### F. Acciones adicionales

Inspecciona las operaciones expuestas por menús, controles contextuales, diálogos, paneles y estados alternativos.

No presupongas que una entidad dispone de todas estas capacidades.

Solo registra funcionalidades sustentadas por evidencias.

## 9. Exploración por roles

No consideres suficiente una sola cuenta cuando existan funcionalidades de colaboración o roles visibles.

El operador autoriza crear las cuentas sintéticas necesarias para explorar relaciones legítimas entre usuarios. No esperes a que se proporcione una segunda cuenta: comprueba el flujo de registro visible y crea por la interfaz las cuentas que permitan cubrir los roles y relaciones observados. Utiliza identidades y credenciales exclusivas de prueba; no las incluyas en evidencias ni documentos.

Por ejemplo:

- Usuario propietario de un recurso sintético.
- Usuario invitado o colaborador.
- Usuario sin participación previa.
- Miembro de un equipo creado para la prueba.

Prepara recursos sintéticos propios y, desde sus controles normales, invita o añade a las cuentas de prueba y configura los permisos disponibles. Cambia de sesión por la interfaz para observar cada contexto: propietario, miembro, invitado o usuario sin participación, según las opciones efectivamente disponibles. Registra una matriz de cuenta/contexto, rol observado, recurso, URL, evidencia y capacidades visibles; distingue los permisos configurados de los comportamientos comprobados.

Si aparecen nuevos roles o niveles de permiso durante el recorrido, incorpora al backlog las exploraciones concretas que habilitan. No declares cubierta la colaboración tras inspeccionarla con una sola cuenta.

No necesitas determinar todavía todas las reglas de autorización.

No intentes adquirir privilegios administrativos mediante mecanismos no autorizados.

Solo marca como bloqueado un rol cuando hayas intentado obtenerlo mediante el registro y los controles legítimos disponibles, o hayas documentado la dependencia técnica concreta que lo impide. No supongas que un rol existe ni adquieras privilegios fuera de los mecanismos expuestos por la aplicación.

## 10. Descubrimiento de funcionalidades transversales

Revisa sistemáticamente todas las áreas de navegación y configuración conocidas.

No dejes pendientes acciones de consulta sencillas.

Incluye los accesos visibles relacionados con:

- Búsqueda.
- Notificaciones.
- Ayuda.
- Atajos de teclado.
- Ajustes.
- Perfil.
- Seguridad.
- Sesiones.
- Vistas.
- Filtros.
- Importación y exportación.
- Integraciones.
- Compartición.
- Personalización.
- Acciones globales.

Abre cada sección accesible e identifica sus capacidades.

Cuando sea necesario crear datos sintéticos para revelar funcionalidades, incorpóralo a la cola y ejecútalo.

No ejecutes operaciones sensibles sin autorización.

## 11. Observación técnica opcional

Playwright MCP será el responsable principal de la navegación.

Chrome DevTools MCP podrá utilizarse para:

- Inspeccionar peticiones y respuestas.
- Identificar capacidades expuestas en datos estructurados.
- Observar eventos relevantes.
- Investigar pistas técnicas concretas.

No es necesario utilizar DevTools en todas las pantallas.

No repitas recorridos únicamente para obtener más información técnica si no existe una hipótesis de descubrimiento relevante.

Cuando ambos MCP compartan navegador:

- Playwright será el único responsable de las interacciones.
- DevTools observará la misma pestaña cuando sea posible.
- No ejecutes acciones simultáneas que puedan interferir.

Si no comparten sesión de forma fiable, utiliza Playwright como herramienta principal y registra la limitación.

Las capacidades identificadas únicamente por información técnica se registrarán como candidatas, hasta que exista evidencia funcional que las corrobore.

## 12. Criterio de saturación funcional

Un área no debe marcarse como EXPLORED simplemente porque hayas visitado todas sus pantallas conocidas.

Debe cumplir:

1. Se visitaron sus puntos de acceso conocidos.
2. Se inspeccionaron sus acciones visibles.
3. Se exploraron los menús contextuales.
4. Se prepararon los datos sintéticos necesarios.
5. Se revisaron los estados vacíos y poblados relevantes.
6. Se investigaron los contextos de usuario accesibles.
7. Se ejecutaron las operaciones habilitadoras necesarias.
8. Se inspeccionaron las nuevas capacidades surgidas.
9. No quedan tareas TODO o IN_PROGRESS accesibles del área.
10. No existen nuevas capacidades descubiertas que requieran otro recorrido contextual.

Cuando un nuevo descubrimiento afecte a una zona previamente explorada, reabre únicamente los contextos relevantes.

Esta condición representa saturación de la superficie observable conocida, no completitud absoluta de la aplicación.

## 13. Política de bloqueo

No aceptes como bloqueo la ausencia de datos, cuentas, roles o permisos que puedes preparar utilizando la propia aplicación sobre recursos sintéticos de prueba. La ausencia inicial de una segunda cuenta no justifica `BLOCKED`.

Antes de marcar una tarea BLOCKED:

1. Identifica la dependencia concreta.
2. Comprueba si puede resolverse mediante la interfaz.
3. Comprueba si puedes preparar datos y cuentas sintéticos mediante la interfaz.
4. Comprueba si puedes asignar el rol o permiso necesario en un recurso sintético propio y acceder con esa cuenta.
5. Comprueba si existe un recorrido alternativo legítimo.
6. Registra los intentos concretos, el resultado y la evidencia de la dependencia que persiste.

Solo considera un bloqueo real cuando no puedas resolverlo dentro de las restricciones.

No informes de una tarea como pendiente si simplemente has decidido no ejecutarla por comodidad o por evitar navegación adicional.

Distingue entre:

- BLOCKED_BY_PERMISSION
- BLOCKED_BY_EXTERNAL_DEPENDENCY
- BLOCKED_BY_TECHNICAL_ERROR
- REQUIRES_EXPLICIT_AUTHORIZATION
- NOT_APPLICABLE

Los bloqueos no justifican dejar sin explorar el resto del módulo.

## 14. Identificación de funcionalidades e historias

Mantén la estructura:

Aplicación → Módulo → Funcionalidad → Historia de usuario.

Para cada funcionalidad registra:

- Identificador estable.
- Nombre.
- Capacidad funcional.
- Módulo.
- Actor observado y estado de sesión (cuenta de prueba o tipo de usuario, autenticado o sin sesión).
- Rol o permiso observado y su ámbito (cuenta, equipo o proyecto), con origen del acceso cuando corresponda: recurso propio, concesión directa o pertenencia a equipo. Si no se muestra un rol específico, registra esa incertidumbre sin asignar uno por analogía.
- Contexto habilitador: recurso, relación del actor con él y estado o dato necesario para que aparezca la capacidad.
- Punto de acceso.
- Evidencia.
- Estado de descubrimiento, distinguiendo control identificado, opciones exploradas y operación ejecutada.

Para cada historia candidata:

- Identificador.
- Funcionalidad padre.
- Actor, estado de sesión, rol o permiso observado con su ámbito y origen de acceso.
- Recurso y contexto habilitador de la capacidad; enlaza la matriz de `roles.md` cuando intervengan permisos o colaboración.
- Capacidad.
- Objetivo, cuando exista evidencia suficiente.
- Evidencia.
- Dependencias.
- Estado IDENTIFIED.

Redacta **la propia frase de cada historia** como «Como [rol, permiso o relación observada con el recurso y su ámbito], quiero [capacidad]»; añade el objetivo solo si existe evidencia suficiente. La frase debe permitir identificar por sí misma quién ejerce la capacidad y en qué ámbito, de forma coherente con las columnas de actor, permiso, contexto y evidencia. Cuando la aplicación no muestre un nombre formal de rol, usa la relación comprobada con el recurso (por ejemplo, creadora de un proyecto o titular de la cuenta propia) y registra la incertidumbre sobre el rol formal en los campos de contexto. Si una historia reúne varias cuentas, expresa únicamente la relación común observada o separa capacidades realmente diferentes, sin atribuir a todas los permisos de una sola.

La redacción debe permitir saber desde qué cuenta y contexto se identificó cada capacidad, sin presentar un permiso configurado como prueba de todas sus acciones ni generalizar lo observado en un recurso a otros roles. Conserva las diferencias entre una opción visible y un resultado ejecutado.

No conviertas cada botón en una historia.

No inventes objetivos de negocio.

No generes todavía criterios de aceptación ni reglas detalladas.

## 15. Inventario incremental

Antes de iniciar el trabajo:

1. Revisa los documentos existentes.
2. Identifica funcionalidades ya descubiertas.
3. Revisa los contextos pendientes.
4. Conserva los identificadores.
5. Construye la cola inicial de exploración.
6. Prioriza las áreas que pueden revelar nuevas capacidades.

No reinicies el inventario.

No dupliques historias.

No elimines funcionalidades sin justificar y registrar la modificación.

## 16. Entregables

Mantén y actualiza:

- `discovery/01-inventory/functional-tree.md`
- `discovery/01-inventory/user-stories.md`
- `discovery/01-inventory/navigation-map.md`
- `discovery/01-inventory/roles.md`
- `discovery/01-inventory/coverage.md`
- `discovery/01-inventory/technical-discovery.md`
- `discovery/01-inventory/discovery-log.md`

Añade:

- `discovery/01-inventory/discovery-backlog.md`

Conserva el registro existente de datos sintéticos y las evidencias en las rutas ya utilizadas por el proyecto.

No cambies la estructura de evidencias sin necesidad.

Cada funcionalidad debe disponer de referencias verificables.

Las tareas del backlog deben tener un resultado o bloqueo documentado.

## 17. Política de eficiencia

Prioriza acciones con alto potencial de descubrir nuevas capacidades.

Agrupa la creación de datos sintéticos por módulo.

Evita repetir recorridos sin nuevos contextos.

Reutiliza sesiones y registros.

No generes capturas redundantes.

Actualiza el inventario incrementalmente para evitar pérdidas de contexto.

No dediques tiempo a investigar exhaustivamente reglas, validaciones, cálculos o errores: pertenecen a fases posteriores.

No utilices herramientas técnicas adicionales cuando la interfaz ya proporcione evidencia suficiente.

No finalices anticipadamente únicamente para reducir el consumo de tokens.

Si existen límites reales de ejecución, herramientas o contexto, conserva el progreso y el backlog pendiente. Informa del motivo y no declares completada la fase.

## 18. Finalización

Antes de finalizar:

1. Revisa el backlog completo.
2. Comprueba que no existan tareas TODO o IN_PROGRESS accesibles.
3. Comprueba que todas las áreas conocidas tengan estado de cobertura justificado.
4. Comprueba que los datos sintéticos necesarios se hayan creado cuando estaba permitido.
5. Comprueba que se hayan explorado las capacidades habilitadas por esos datos.
6. Comprueba que los roles y relaciones accesibles se hayan explorado con cuentas sintéticas cuando era necesario.
7. Comprueba que no existan identificadores duplicados.
8. Verifica la consistencia documental.
9. Registra los bloqueos reales.
10. Identifica qué funcionalidades se han descubierto durante esta ejecución.
11. Comprueba que no quedan tareas de descubrimiento accesibles cuya ejecución pueda revelar capacidades adicionales.

El estado final será:

- COMPLETE_KNOWN_SURFACE: todos los contextos conocidos, accesibles y autorizados han alcanzado saturación funcional.
- PARTIAL_BLOCKED: solo permanecen contextos no accesibles por bloqueos justificados.
- PARTIAL_IN_PROGRESS: existen exploraciones accesibles todavía pendientes.

No utilices COMPLETE_KNOWN_SURFACE como afirmación de cobertura absoluta sobre funcionalidades desconocidas.

## 19. Informe final

Presenta:

- Módulos identificados.
- Funcionalidades confirmadas.
- Historias candidatas.
- Nuevas funcionalidades descubiertas.
- Contextos explorados.
- Usuarios y roles utilizados.
- Tareas completadas.
- Tareas pendientes.
- Bloqueos reales.
- Estado de saturación funcional.
- Limitaciones de las herramientas.
- Próximas acciones concretas.

**No finalices la exploración mientras queden tareas accesibles en el backlog y dispongas de capacidad para ejecutarlas.**

**No inicies la fase de análisis funcional detallado.**

**No generes especificaciones técnicas exhaustivas ni código.**
