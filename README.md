# Introducción

Este proyecto es una prueba de concepto (PoC) de descubrimiento funcional de aplicaciones mediante agentes de Codex. El objetivo es generar un inventario de funcionalidades y evaluar su cobertura.

Para ello se basa en la aplicacion de ejemplo Vikunja, que se ejecuta en un contenedor Docker y se accede mediante un navegador web. 

Los agentes se comunican con el navegador mediante el protocolo de depuración remota, usando dos MCP: Playwright y Chrome DevTools. El primero realiza las interacciones y el segundo observa la misma pestaña de forma secuencial.

# Arranque de la aplicación

Para iniciar la aplicación, ejecute el siguiente comando en el directorio donde se encuentra el archivo `docker-compose.yaml`:

```bash
docker compose up -d
```

Accede a la siguiente URL:

```text
http://localhost:3456/
```

# Herramientas de navegador para el discovery

Playwright MCP y Chrome DevTools MCP pueden conectarse al mismo Chrome mediante el protocolo de depuración. En esta PoC, Playwright realiza las interacciones y DevTools observa la misma pestaña de forma secuencial. No cierres el Chrome compartido desde ninguno de los MCP mientras el otro lo utilice.

## 1. Comprobar requisitos

Se necesitan Node.js LTS, npm, Codex CLI y Google Chrome. Comprueba que están disponibles en PowerShell:

```powershell
node --version
npm --version
codex --version
Test-Path 'C:\Program Files\Google\Chrome\Application\chrome.exe'
```

La última línea debe devolver `True`. Ajusta la ruta de Chrome si está instalado en otra ubicación.

## 2. Iniciar un Chrome dedicado

Un **perfil de Chrome** es la carpeta donde el navegador guarda cookies, sesiones y preferencias. Aquí usamos una carpeta exclusiva para las pruebas de Vikunja, distinta de tu perfil habitual. Chrome la crea automáticamente al abrirse; no requiere una cuenta de Chrome. Las cuentas sintéticas de Vikunja para explorar roles se crean después mediante la interfaz de la aplicación. Así, ambos MCP pueden conectarse a la misma sesión de prueba. La carpeta se guarda fuera del repositorio.

Con Vikunja disponible en `http://localhost:3456/`, copia **esta línea completa** en PowerShell y pulsa Enter una vez:

```powershell
& 'C:\Program Files\Google\Chrome\Application\chrome.exe' --remote-debugging-address=127.0.0.1 --remote-debugging-port=9222 --user-data-dir="$env:LOCALAPPDATA\REA\chrome-discovery" 'http://localhost:3456/'
```

Puedes comprobar el puerto antes de arrancar Chrome (se espera `False` si está libre) y después (se espera `True`):

```powershell
Test-NetConnection 127.0.0.1 -Port 9222
```

`TcpTestSucceeded` debe ser `True` después de arrancar Chrome. El puerto de depuración permite controlar el navegador: usa este perfil solo con datos de prueba y cierra Chrome al terminar.

## 3. Configurar ambos MCP en Codex

El proyecto ya incluye [`.codex/config.toml`](.codex/config.toml) con los dos servidores MCP. Playwright usa `--cdp-endpoint` y Chrome DevTools usa `--browser-url`, ambos dirigidos al Chrome dedicado en `127.0.0.1:9222`. Esta configuración pertenece a REA y no modifica `$HOME\.codex\config.toml`.

Abre REA como proyecto de confianza en Codex para que cargue el archivo local. Inicia primero el Chrome del punto 2; después, reinicia Codex desde este proyecto y comprueba que los dos servidores aparecen configurados:

```powershell
codex mcp list
```

Antes de empezar un recorrido, comprueba con las herramientas de ambos MCP que ven la misma pestaña de Vikunja y el mismo contexto de usuario. Si Codex no consigue iniciar `npx` en Windows 11, consulta la [configuración de Windows para Codex](https://github.com/ChromeDevTools/chrome-devtools-mcp/blob/main/docs/client-configurations.md#codex).

Las opciones de conexión están descritas en las guías oficiales de [Playwright MCP](https://github.com/microsoft/playwright-mcp/blob/main/README.md) y [Chrome DevTools MCP](https://github.com/ChromeDevTools/chrome-devtools-mcp/blob/main/docs/advanced-usage.md#connecting-to-a-running-chrome-instance).

## Uso por fases

### Exploración y auditoría del inventario

El agente configurado en `.codex/agents/document-auditor.toml` se llama `inventory_auditor`. El nombre del archivo y el nombre del agente son distintos; utiliza el nombre configurado al delegar.

Prompt de coordinación para este recorrido:

> Explora Vikunja y actualiza el inventario funcional existente.
>
> 1. Comprueba que Chrome funciona en el puerto 9222, que la pestaña activa contiene Vikunja y que Playwright MCP y Chrome DevTools MCP están conectados al mismo navegador. Mantén Chrome abierto durante el recorrido.
> 2. Delega la exploración al subagente `functional_explorer` de `.codex/agents/functional-explorer.toml`, siguiendo `prompts/00-descubrimiento.md`. El operador autoriza crear por la interfaz las cuentas y datos sintéticos necesarios, configurar roles y permisos de esas cuentas sobre recursos sintéticos propios y cambiar de sesión para explorar cada contexto. Conserva el inventario y los identificadores previos.
> 3. Cuando termine una entrega del explorador, delega su auditoría documental al subagente `inventory_auditor` de `.codex/agents/document-auditor.toml`, siguiendo `prompts/01-auditoria-descubrimiento.md`. El auditor no navega; decide si las evidencias justifican la cobertura y propone exploraciones concretas con causa y objetivo.
> 4. Repite como máximo tres ciclos de revisión explorador–auditor, con auditorías incrementales que conserven el historial de hallazgos. Informa del estado real de cobertura al final, aunque queden límites justificados.
>
> El agente principal solo coordina; no realiza la exploración ni la auditoría. No avances automáticamente a análisis funcional o especificación.
