## Restricciones de descubrimiento

### 3.1. Fuentes permitidas

Puedes utilizar exclusivamente:

- La interfaz visual renderizada en el navegador.
- Los elementos DOM y el árbol de accesibilidad de las páginas visitadas.
- Las interacciones del usuario reproducidas mediante automatización del navegador.
- Las URL y rutas observadas durante la navegación.
- Los mensajes, errores, notificaciones y estados visibles.
- El tráfico HTTP generado por el navegador durante operaciones autorizadas, únicamente en las fases en las que se solicite su análisis.
- Las capturas de pantalla y trazas producidas durante la navegación.
- Descargar los fuentes de recursos estáticos (HTML, CSS, JS, imágenes...) únicamente para su análisis en el contexto de la fase de descubrimiento.

Puedes utilizar REA, Playwright y herramientas basadas en CDP como mecanismos de observación dentro de estos límites.

### 3.2. Fuentes expresamente prohibidas

No puedes:

- Leer, clonar, descargar o consultar el repositorio fuente de Vikunja.
- Utilizar herramientas de decompilación o análisis estático de artefactos que no estén expuestos a través del navegador.
- Inspeccionar binarios, ejecutables o imágenes de contenedores.
- Consultar bases de datos, volúmenes o sistemas de archivos de la aplicación.
- Acceder al backend directamente desde terminal, scripts o clientes HTTP independientes.
- Consultar documentación oficial, OpenAPI, Swagger, repositorios externos o información pública sobre Vikunja.
- Utilizar conocimiento previo sobre la implementación de Vikunja como evidencia.
- Consultar herramientas administrativas del hosting, Docker, Podman o infraestructura.
- Acceder a rutas, endpoints o recursos que no hayan aparecido durante una navegación autorizada.
- Intentar descubrir recursos ocultos mediante fuerza bruta, fuzzing o enumeración indiscriminada.

El hecho de que una herramienta permita realizar una operación no implica que esté autorizada.

### 3.3. Prohibición de implementación

No debes generar:

- Código fuente de la aplicación de reemplazo.
- Componentes frontend.
- Servicios backend.
- Scripts de implementación.
- Migraciones de bases de datos.
- Infraestructura de despliegue.

Los artefactos técnicos autorizados son exclusivamente especificaciones, modelos, diagramas y contratos documentales.