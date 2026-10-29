# Fase 3 — Análisis de una historia de usuario

Historia objetivo: `[US-ID]`. Sustituye el marcador por un único ID indicado por el operador. Si falta, no existe en `discovery/01-inventory/user-stories.md` o apunta a más de una historia, detén el análisis y solicita el ID correcto. La ejecución de este prompt requiere que el operador haya autorizado expresamente la Fase 3.

## Alcance y fuentes

Reconstruye el comportamiento observable de **esa historia**, sin analizar otras US salvo las dependencias imprescindibles para preparar o interpretar sus escenarios. Identifica su FUN y MOD, la frase candidata, sus columnas de actor, rol/permiso, contexto y EV, y contrástalas con `functional-tree.md`, `roles.md`, `coverage.md` y el material previo. Si la historia agrupa capacidades distintas, delimita qué parte se observa en cada escenario; no cambies su ID ni amplíes el encargo por iniciativa propia.

Cumple `AGENTS.md` y `prompts/common/restrictions.md`. Observa la aplicación exclusivamente mediante el navegador: interfaz renderizada, DOM/accesibilidad, URL y tráfico originado por interacciones legítimas cuando aporte evidencia al comportamiento. No consultes código fuente, bundles, repositorios, base de datos, contenedores, documentación externa ni endpoints invocados fuera del navegador. No uses la existencia de una API como prueba de acceso funcional.

## Preparación del contexto

1. Registra cuenta o tipo de actor, estado de sesión, rol o permiso **observado**, ámbito del permiso, origen del acceso (recurso propio, concesión directa o pertenencia a equipo), recurso y estado de los datos. Distingue un valor configurado de una capacidad comprobada. Si no hay etiqueta formal de rol, usa la relación observada y deja la etiqueta formal como `UNKNOWN`.
2. Identifica los contextos de usuario y de datos que podrían cambiar **esta** capacidad. Prepara por la interfaz cuentas y recursos sintéticos propios cuando sean necesarios; el operador autorizó su creación y la configuración de sus permisos. La ausencia inicial de una cuenta o rol preparable no es un bloqueo.
3. Diseña una lista corta de escenarios pertinentes: flujo principal, alternativas, entradas o estados límite, errores observables y diferencias de permiso que afecten a la US. Registra para cada uno la hipótesis o pregunta, precondición, actor, recurso, acción y observación buscada. No impongas una matriz cartesiana de todos los roles y valores si no aporta información a la historia.

## Ejecución

Recorre el flujo principal desde su punto de entrada y observa el resultado. Investiga después las ramas relevantes y las nuevas acciones habilitadas. Para cada escenario registra datos sintéticos usados, estado anterior, pasos ejecutados, mensajes y controles, resultado inmediato, estado posterior y persistencia cuando corresponda (por ejemplo, al volver a la vista o sesión). Un control visible, un formulario abierto y una operación completada son evidencias diferentes. No infieras que un campo es obligatorio, que una regla se aplica siempre o que un cambio persistió sin una comprobación específica.

Analiza solo lo que afecte a la US: precondiciones, campos y valores por defecto, validaciones, alternativas, excepciones, cálculos visibles, transiciones de estado y consecuencias observables. Si aparece una dependencia de otra historia, enlázala y registra qué dato necesitas de ella, sin ejecutar su análisis completo. Repite una operación cuando una hipótesis importante siga sin resolverse y el nuevo escenario pueda aportar evidencia distinta.

Clasifica antes de actuar. Puedes navegar y modificar cuentas o recursos sintéticos propios mediante controles legítimos. **Una acción destructiva requiere autorización expresa incluso sobre datos de prueba**; no ejecutes operaciones sobre cuentas o recursos ajenos ni cambios globales sensibles. Acciones con efectos externos, secretos, credenciales reales o envío a terceros requieren autorización específica. Si una rama no está autorizada, documenta el control y la dependencia sin confirmar su efecto. No guardes contraseñas, tokens, correos reales ni secretos en documentos o evidencias.

## Evidencia y precisión

Conserva las nuevas EV en `discovery/01-inventory/evidences/`, con ID estable, URL, fecha/hora, cuenta o actor, rol/permiso y ámbito, origen de acceso, recurso, estado previo, acción y resultado observado. Actualiza el índice de EV y el registro de actividad sintética cuando corresponda. Usa referencias concretas desde el análisis; no reconstruyas una evidencia ausente. Una expectativa de prueba es una hipótesis, no un resultado.

Clasifica **cada afirmación relevante**, no el documento entero, como `OBSERVED`, `INFERRED`, `UNKNOWN` o `VALIDATED` según `AGENTS.md`. Relaciona una afirmación `VALIDATED` con la prueba específica que la confirmó; conserva las excepciones y límites de contexto. No generalices desde una cuenta, permiso, recurso o valor a otros sin evidencia. Si dos estados parecen iguales, comprueba sus acciones o resultados antes de declararlos equivalentes.

## Entregable de análisis

Mantén `discovery/02-analysis/modules/[MOD-ID]/[US-ID].md` como **dossier de Fase 3**, no como especificación formal de Fase 4. Incluye, de forma compacta:

- ID y texto de la US, FUN/MOD, alcance, dependencias y estado del dossier.
- Actor y matriz de contextos realmente preparados: sesión, rol/permiso y ámbito, origen de acceso, recurso/estado y EV.
- Escenarios ejecutados y pendientes, con precondición, acción, resultado y persistencia; flujo principal, alternativas y excepciones pertinentes.
- Afirmaciones trazables sobre interfaz, comportamiento, validaciones, estados, cálculos y posibles reglas, cada una con clasificación y EV; separa hipótesis de reglas comprobadas.
- Limitaciones, incertidumbres, preguntas abiertas y siguiente acción concreta para cada hueco accesible o bloqueo real.

Conserva los IDs y la documentación anterior. Mantén **dos estados distintos**:

- **Estado provisional del dossier:** `READY_FOR_AUDIT` solo si consideras cubiertos los escenarios conocidos y accesibles de la US; `PARTIAL_IN_PROGRESS` si quedan escenarios pertinentes accesibles; `PARTIAL_BLOCKED` si únicamente quedan dependencias concretas irresolubles o acciones que requieren autorización expresa. Documenta los motivos y remite el dossier al auditor **también cuando sea parcial**, para que examine la causa y proponga la siguiente exploración.
- **Estado de análisis de la US en el inventario:** añade la columna individual `Estado de análisis` en `user-stories.md` al iniciar la primera US, si falta; adapta la nota de cabecera que actualmente declara un estado común y conserva las demás US como `IDENTIFIED`. Marca solo la US objetivo como `IN_ANALYSIS` mientras trabajas o revisas un dictamen parcial. Nunca traslades `READY_FOR_AUDIT` a esa columna ni marques la US como analizada por haber redactado el dossier. Después de cada auditoría, el auditor fijará allí su veredicto sobre esa US.

Remite cada entrega a `prompts/03-auditoria-us.md`, incluida una entrega parcial, y conserva el veredicto previo del auditor como historial en su informe.

Finaliza tu turno con la cobertura lograda, EV nuevas, escenarios pendientes, bloqueos y preguntas que debe examinar el auditor. No declares completitud absoluta, no generes código y no avances automáticamente a otra historia o fase.
