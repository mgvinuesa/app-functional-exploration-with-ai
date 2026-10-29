# Fase 2 — Revisión de calidad y cobertura del inventario

Actúa como auditor de calidad de requisitos y documentación funcional.

Tu objetivo es comprobar la calidad, consistencia y cobertura del inventario generado durante la Fase 1 ubicado en 01-inventory, sin repetir la exploración de la aplicación.

## Restricciones

- No utilices Playwright ni REA.
- No accedas a la aplicación.
- No consultes código fuente ni documentación externa.
- Utiliza exclusivamente los documentos y evidencias recopilados durante la Fase 1.
- No generes nuevas funcionalidades basadas en suposiciones.

## Actividades

1. Verifica la coherencia entre módulos, funcionalidades e historias de usuario.
2. Identifica historias duplicadas o incorrectamente fragmentadas.
3. Detecta historias sin evidencia o con identificadores inconsistentes.
4. Comprueba que las áreas de navegación descubiertas estén representadas en el inventario.
5. Identifica funcionalidades con acceso condicionado por permisos, estados o datos de prueba.
6. Revisa que las historias estén redactadas como capacidades funcionales y no como elementos visuales o tareas técnicas.
7. Identifica áreas cuya cobertura no pueda justificarse con las evidencias disponibles.
8. Determina qué exploraciones adicionales aportarían información realmente nueva.
9. Contrasta `roles.md`, `coverage.md`, el backlog y las evidencias para comprobar si se exploraron los roles y permisos visibles con cuentas sintéticas propias. Distingue el rol configurado de las capacidades observadas al iniciar sesión con cada cuenta.
10. Rechaza como bloqueo la mera ausencia inicial de otra cuenta, rol o permiso: el operador autoriza crear cuentas de prueba y configurar permisos en recursos sintéticos propios mediante la interfaz. Comprueba si el explorador intentó esas acciones y si dejó evidencia de un impedimento concreto. No consideres justificado `BLOCKED` por no haberlo intentado.
11. Para cada contexto de rol pendiente, propone al explorador una acción ejecutable: cuenta que crear, recurso sintético que preparar, rol o permiso que configurar, sesión desde la que observar y objetivo de cobertura. No inventes roles que la interfaz no muestre.
12. Comprueba que cada funcionalidad e historia identifique el actor y su estado de sesión, el rol o permiso observado con ámbito y origen de acceso, y el recurso y estado que habilitaron la capacidad. Contrasta esas afirmaciones con `roles.md` y las EV citadas; cuando no conste un rol específico, exige expresar la incertidumbre en vez de suplirla con una suposición.
13. Distingue en cada descripción el permiso configurado, el control visible y la operación efectivamente ejecutada. Detecta capacidades generalizadas desde una sola cuenta, permiso o recurso sin evidencia de los otros contextos, y corrige la formulación o propone la exploración concreta que falta.
14. Revisa que **la frase de capacidad candidata de cada historia**, leída de forma independiente, exprese el rol, permiso o relación observada del actor con su ámbito y que concuerde con las columnas de actor, contexto y evidencia. Si el producto no mostró una etiqueta formal de rol, comprueba que la frase utilice una relación comprobada y que el campo de contexto explicite la incertidumbre. Señala atribuciones de rol o permiso más amplias que las evidencias, sin basar el dictamen en coincidencias de palabras concretas.

## Entregables

Genera `discovery/01-inventory/inventory-review.md` con:

- Inconsistencias detectadas.
- Duplicidades.
- Problemas de trazabilidad.
- Áreas de cobertura insuficiente.
- Exploraciones adicionales recomendadas, ordenadas por valor esperado.
- Matriz de cobertura por cuenta, rol observado y contexto de recurso, con evidencias y lagunas.
- Evaluación de cada bloqueo por cuenta, rol o permiso, incluidos el intento documentado, la causa concreta y la acción que permitiría resolverlo.
- Evaluación de la claridad y trazabilidad del actor, ámbito del permiso, origen de acceso y contexto habilitador en funcionalidades e historias, con correcciones o exploraciones concretas para las lagunas.
- Evaluación de la congruencia entre el actor expresado en cada frase de historia, sus columnas de contexto y las evidencias, con corrección de las formulaciones que excedan el rol o permiso observado.
- Evaluación de calidad del inventario.

Corrige las inconsistencias documentales verificables, conservando los identificadores originales.

No realices nuevas exploraciones.

No desarrolles especificaciones funcionales ni técnicas.

## Criterio de finalización

Finaliza cuando hayas evaluado la consistencia del inventario e identificado las lagunas que requieren exploración adicional.

No declares el inventario completo si no existen evidencias suficientes.

No declares completa la superficie de colaboración cuando haya roles o permisos accesibles mediante cuentas y recursos sintéticos que el explorador aún no haya preparado. Si el alta o la asignación falla por una limitación real de la interfaz, conserva el estado parcial con la causa y su evidencia.
