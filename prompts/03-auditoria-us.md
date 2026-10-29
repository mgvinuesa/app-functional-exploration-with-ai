# Fase 3 — Auditoría incremental del análisis de una historia de usuario

Historia objetivo: `[US-ID]`. Audita **solo** el dossier `discovery/02-analysis/modules/[MOD-ID]/[US-ID].md` y sus dependencias documentales necesarias. Usa el mismo ID, FUN y MOD que constan en el inventario. Si falta el dossier o el ID no coincide, informa del impedimento documental; no analices otra US ni completes el dossier inventando observaciones.

## Límites y fuentes

Tu trabajo es documental. No uses Playwright, Chrome DevTools, REA ni el navegador; no accedas a Vikunja, al código fuente, a APIs o a documentación externa. Consulta `AGENTS.md`, `prompts/common/restrictions.md`, la fila de la US, su FUN/MOD, `roles.md`, `coverage.md`, las EV citadas, el registro de datos sintéticos y las versiones previas del dossier y de esta auditoría. Conserva los IDs y la historia de revisiones. No inicies la Fase 4 ni redactes especificaciones formales.

## Comprobaciones

1. **Alcance:** el dossier responde a la capacidad de la US y no transforma dependencias u otras historias en objetivos nuevos. La frase de la US, actor y contexto concuerdan con el inventario o las diferencias están justificadas por EV nuevas.
2. **Contextos:** para cada escenario constan sesión/actor, rol o permiso observado con ámbito, origen del acceso (propio, directo o por equipo), recurso, datos y estado habilitador. Distingue permiso configurado de capacidad comprobada; no deduzcas un rol formal inexistente. Si faltan cuentas o permisos preparables sobre recursos sintéticos, exige la preparación por interfaz antes de aceptar un bloqueo.
3. **Cobertura de la US:** comprueba flujo principal, alternativas, validaciones, errores, límites, transiciones y persistencia **cuando sean pertinentes**. Verifica que una pantalla, un control, un intento y una operación completada no se presentan como equivalentes. No exijas pruebas exhaustivas ajenas al alcance ni aceptes un flujo principal pendiente que siga siendo accesible.
4. **Trazabilidad:** contrasta cada afirmación importante y su clasificación `OBSERVED`, `INFERRED`, `UNKNOWN` o `VALIDATED` con EV legibles. Las EV deben permitir identificar URL, momento, actor/permiso, recurso, acción, antes/después y resultado; un nombre de archivo o una hipótesis no prueba el resultado. Señala referencias erróneas, duplicadas o evidencia transitoria insuficiente.
5. **Consistencia y límites:** detecta contradicciones entre dossier, US/FUN, matriz de roles, actividad sintética y EV. Revisa que los resultados no se extrapolen a otros roles, recursos o estados; que la incertidumbre siga explícita; y que no se hayan registrado secretos o datos ajenos. Distingue un bloqueo real de una exploración omitida o de una acción deliberadamente no autorizada.

Corrige inconsistencias **puramente documentales y verificables** conservando IDs y texto histórico. No alteres evidencias originales ni sustituyas observaciones mediante inferencias. Una laguna que requiera navegar se devuelve al analista.

## Informe por US y tareas de revisión

Mantén `discovery/02-analysis/modules/[MOD-ID]/[US-ID]-review.md`. En la primera auditoría crea la línea de base; en las siguientes añade una sección incremental con hallazgos nuevos, resolución de los anteriores y conversación de decisiones analista–auditor. No sobrescribas dictámenes históricos: señala cuál es el **veredicto vigente**.

Incluye evaluación de alcance, coherencia de actor/permiso, cobertura de escenarios, calidad de evidencia y clasificación de afirmaciones; inconsistencias corregidas; huecos y bloqueos justificados. Para cada exploración adicional, propone una tarea **ejecutable y priorizada** con causa, escenario, cuenta/permiso/ámbito, recurso y datos sintéticos necesarios, acción de navegador, observación esperada como hipótesis y EV que debería conservarse. No inventes un resultado esperado como hecho. Si una acción requiere autorización expresa, indícala y propone lo que puede documentarse sin ejecutarla.

## Ciclo y decisión

El ciclo es **analista → auditor → analista** para la misma US. Realiza una auditoría inicial y, si quedan huecos abordables, **hasta tres ciclos adicionales de revisión analista–auditor**; el máximo es cuatro auditorías de esa US contando la inicial. Tras cada dictamen no final, el coordinador devuelve al analista tareas concretas y solicita una revisión incremental. No audites un incremento sin nuevas evidencias o correcciones que respondan a un hallazgo. Al agotar los tres ciclos adicionales emite el veredicto real aunque queden límites; no inicies otro ciclo automáticamente.

Comprueba el **estado provisional del dossier** (`READY_FOR_AUDIT`, `PARTIAL_IN_PROGRESS` o `PARTIAL_BLOCKED`), pero emite tu propia decisión a partir de documentos y EV. El estado provisional describe la cobertura declarada por el analista y **no se copia automáticamente** al inventario. Usa un único veredicto vigente:

- `ANALYZED_KNOWN_SURFACE`: los escenarios pertinentes, conocidos y accesibles de esta US tienen evidencia suficiente para Fase 3; no implica especificación final ni completitud absoluta.
- `PARTIAL_IN_PROGRESS`: permanece al menos un escenario accesible y relevante sin analizar o sin evidencia suficiente.
- `PARTIAL_BLOCKED`: solo quedan escenarios relevantes impedidos por una dependencia concreta y documentada o por una acción que requiere autorización expresa.

La ausencia de cuentas, roles, permisos o datos que pueden prepararse legítimamente por la UI no justifica `PARTIAL_BLOCKED`. Actualiza **solo la columna `Estado de análisis` de la US objetivo** en `user-stories.md` con tu veredicto: `ANALYZED_KNOWN_SURFACE`, `PARTIAL_IN_PROGRESS` o `PARTIAL_BLOCKED`. Si la columna aún no existe, créala, adapta la nota de cabecera y conserva las demás US como `IDENTIFIED`. Una US parcial queda abierta y el informe detalla las condiciones para continuar; cuando el analista retome esa US, volverá a `IN_ANALYSIS` hasta el siguiente dictamen. El auditor decide la suficiencia documental; no navega, no crea datos y no avanza de fase.
