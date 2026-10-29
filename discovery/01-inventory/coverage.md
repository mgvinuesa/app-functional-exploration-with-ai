# Cobertura del inventario

Estado: `COMPLETE_KNOWN_SURFACE` para las superficies funcionales conocidas, accesibles y autorizadas observadas en Fase 1. DQ-21 quedó DONE; el backlog no contiene TODO, IN_PROGRESS ni BLOCKED. Esto no representa cobertura absoluta ni validación de reglas.

Las áreas siguientes agregan observaciones de varias sesiones y permisos. La matriz de `roles.md` y los contextos de `user-stories.md` identifican la cuenta, el origen del acceso y el recurso para cada capacidad; la presencia de una opción en un contexto no se extrapola a los demás.

| Área | Estado | Cobertura observada | Límite explícito |
|---|---|---|---|
| Resumen / tareas | OBSERVADA | Alta rápida, detalle y acciones; tarea asignada a segunda cuenta; opciones de progreso, relación, movimiento, adjunto y recordatorio; acceso compartido directo y por equipo | No se aplicaron estados/properties adicionales de tarea durante la comparación |
| Próximas | OBSERVADA | Estado vacío y poblado, intervalo y controles de rango/visibilidad | Sin exploración accesible pendiente identificada |
| Proyectos | OBSERVADA | Alta, cuatro vistas, filtros, buckets, menú, ajustes, webhooks, compartir directo y por equipo; permisos directos y por equipo Read only/Read & write/Admin comparados; menú/tarea observados como miembro por equipo | Alta efectiva de bucket UNKNOWN; no se ejecutaron acciones destructivas ni integraciones |
| Etiquetas | OBSERVADA | Alta sintética, listado/edición y asociación a tarea | Sin exploración accesible pendiente identificada |
| Equipos/colaboración | OBSERVADA | Registro de cuenta secundaria; miembro/Admin de equipo; compartir proyecto con equipo en los tres niveles; capacidades de miembro observadas bajo Read only, Read & write y Admin; prueba de URL sin participación | No se observó rol global alternativo |
| Búsqueda/acción rápida | OBSERVADA | Modal, comandos y alcances `+` proyectos, `@` equipos, `*` etiquetas | Resultado de tarea exacta no observado |
| Notificaciones | OBSERVADA | Estado vacío y avisos no leídos de alta al equipo/asignación, con acciones visibles | No se limpiaron ni marcaron como leídos |
| Cuenta/perfil/ajustes | PARCIAL | Pantallas informativas de perfil, seguridad, datos, integraciones y eliminación | No se introdujeron credenciales, emitieron/revocaron tokens/sesiones, crearon integraciones, importaron datos ni confirmaron eliminación |
| Importación de datos | OBSERVADA | Proveedores, formulario CSV, selector de archivo y mapeo | No se eligió archivo ni se inició importación |
| Atajos/ayuda | OBSERVADA | Ayuda de prefijos y atajos globales/contextuales | Sin exploración accesible pendiente identificada |

## Acceso y colaboración

La matriz detallada está en `roles.md`. DQ-18 aisló el acceso de equipo retirando temporalmente el permiso directo. DQ-21 observó, como miembro, controles de lectura bajo Read only, alta/estado habilitados y menú sin Eliminar bajo Read & write, y menú con Eliminar bajo Admin; los controles de tarea se mantuvieron visibles en ambos contextos sin ejecutarlos. Se retiró la concesión de equipo y se restauró el permiso directo Read & write. DQ-19 comparó el menú directo Read & write con Admin y capturó el selector final. DQ-20 encontró el aviso UI de falta de permiso al abrir rutas conocidas de recursos sintéticos no compartidos; no se infiere estado HTTP ni regla universal.

Persisten límites de operación fuera del inventario autorizado: no se confirmó eliminación/archivo, enlaces públicos, webhooks, emisión o revocación de tokens, importación ni borrado de cuenta. El resultado de creación de bucket, ciertos resultados de búsqueda y roles globales no visibles permanecen UNKNOWN. La cobertura documenta opciones y controles visibles sin probar reglas generales de autorización.
