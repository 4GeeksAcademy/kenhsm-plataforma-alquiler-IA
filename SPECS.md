# SPECS — Prototipo Panel Admin de AgentHub

Versión: v1.0
Fecha: 2026-08-05

## 1) Descripción del producto
AgentHub es una plataforma SaaS para alquilar agentes de IA preconfigurados, a los que se les pueden activar skills para resolver tareas de negocio.

Este entregable corresponde al panel de administración interno usado por el equipo de operaciones de AgentHub (rol: administrador). El objetivo es visualizar estado de negocio, gestionar usuarios/agentes/skills, revisar contratos y atender errores operativos.

El prototipo es de alta fidelidad visual, con datos hardcodeados y sin integración de backend.

## 2) Stack y restricciones técnicas
1. Se implementa en HTML5 semántico.
2. Se usa Tailwind CSS cargado exclusivamente vía CDN.
3. Toda interactividad se implementa con JavaScript vanilla (sin React, Vue, Angular, jQuery, ni build tools).
4. No se permite CSS externo ni embebido personalizado para estilos de UI; la composición visual se resuelve con utilidades de Tailwind.
5. No hay llamadas HTTP ni consumo de API. Todos los datos se hardcodean en el frontend.
6. Debe existir soporte responsive para mobile y desktop.

## 3) Layout global y navegación
1. El layout principal usa sidebar persistente a la izquierda (desktop) y navegación visible/usable en mobile.
2. La parte superior del contenido incluye barra con título de sección y toggle claro/oscuro.
3. La navegación contiene exactamente seis entradas: Dashboard, Gestión de usuarios, Gestión de agentes, Skills, Contrataciones, Log de errores.
4. El ítem activo de navegación debe mostrarse con estilo diferenciado (fondo/acento/tipografía).
5. Cada sección se muestra sin recarga completa (vista única con secciones conmutables).

## 4) Especificaciones por sección

### 4.1 Dashboard
1. Mostrar 4 tarjetas de métricas en grid responsive (1 columna en mobile, 2 en tablet, 4 en desktop) con icono, etiqueta y valor hardcodeado: ingresos del mes, pérdida por descuentos, agentes activos, agentes fallando.
2. Cada tarjeta usa color de acento distinto y contraste legible en claro/oscuro.
3. Debajo de las tarjetas, mostrar un bloque de ancho completo como placeholder del gráfico semanal, con etiqueta centrada y marcas de días.
4. Agregar un bloque secundario de actividad reciente (lista breve) para reforzar utilidad de la vista inicial.

### 4.2 Gestión de usuarios
1. Tabla responsive con al menos 5 usuarios hardcodeados y columnas: nombre, email, plan, estado.
2. El estado se representa con badge de color (activo, pendiente, suspendido).
3. Cada fila incluye botón de acciones `⋮` que abre dropdown contextual con opciones "Ver detalle" y "Eliminar".
4. "Ver detalle" abre modal overlay con ficha completa del usuario (nombre, email, plan, estado, fecha de alta, último acceso).
5. El modal se cierra mediante botón de cierre y clic en backdrop.

### 4.3 Gestión de agentes
1. Listado de al menos 4 agentes con nombre, propietario y badge de estado (activo/inactivo/fallando).
2. Cada agente incluye control expandible para mostrar/ocultar skills asociadas; por defecto debe iniciar colapsado.
3. La expansión/colapso de skills debe animarse suavemente (transición de altura/opacidad).
4. Cada agente tiene dropdown `⋮` con "Configurar" y "Eliminar".
5. "Configurar" abre modal con textarea editable que contiene el prompt de sistema del agente.

### 4.4 Skills
1. Mostrar catálogo con al menos 4 skills en tarjetas/listado, cada una con nombre, descripción y contador de agentes habilitados.
2. Incluir bloque explicativo breve sobre qué es una skill dentro del contexto AgentHub.
3. Cada skill incluye dropdown `⋮` con "Ver detalle" y "Eliminar".
4. "Ver detalle" abre modal con descripción extendida, casos de uso y metadatos básicos.

### 4.5 Contrataciones de agentes
1. Tabla con al menos 4 contratos mostrando cliente, agente, skills contratadas, fechas inicio/fin e importe pagado.
2. El campo skills se presenta de forma resumida legible (chips o texto compacto).
3. Cada fila contiene dropdown `⋮`; "Ver detalle" abre modal con desglose completo del contrato.
4. El desglose incluye lista itemizada de skills contratadas con precio individual y subtotal.

### 4.6 Log de errores
1. Mostrar al menos 6 entradas hardcodeadas con timestamp, agente, tipo de error y descripción breve.
2. El tipo/gravedad usa badges con código de color consistente (crítico, warning, info).
3. Cada entrada incluye dropdown `⋮` con "Ver detalle" y "Marcar como resuelto".
4. "Ver detalle" abre modal con traza completa y contexto del error.

## 5) Inventario de componentes reutilizables
1. Sidebar de navegación persistente.
2. Header superior con título contextual y toggle de tema.
3. Tarjeta de métrica KPI.
4. Tabla de datos responsive.
5. Badge de estado/tipo (usuarios, agentes, severidad de errores).
6. Dropdown de acciones por fila/tarjeta.
7. Modal overlay reutilizable con cierre por botón/backdrop.
8. Lista colapsable de skills por agente.
9. Chips de skills contratadas.
10. Textarea editable para prompt de configuración del agente.

## 6) Reglas de interacción global
1. Toggle claro/oscuro aplica clase `dark` sobre el documento y persiste preferencia en `localStorage`.
2. Todos los dropdowns se cierran al hacer clic fuera de su contenedor.
3. Solo un dropdown por contexto puede permanecer abierto al mismo tiempo.
4. Todos los modales se cierran al hacer clic en backdrop.
5. Los modales deben bloquear foco visual del fondo con overlay semitransparente.
6. La navegación actualiza el estado activo del sidebar y el título superior de sección.

## 7) Datos hardcodeados mínimos
1. Usuarios: 5 o más.
2. Agentes: 4 o más.
3. Skills catálogo: 4 o más.
4. Contratos: 4 o más.
5. Logs de error: 6 o más.

## 8) Criterios de aceptación verificables
1. Existe sidebar persistente con 6 secciones y estado activo visible.
2. El Dashboard muestra exactamente 4 KPIs y un placeholder de actividad semanal.
3. La tabla de usuarios contiene al menos 5 filas y dropdown funcional por fila.
4. En usuarios, la acción "Ver detalle" abre modal con datos completos y cierra por botón y backdrop.
5. El listado de agentes contiene al menos 4 elementos y skills colapsadas por defecto.
6. La expansión de skills en agentes ocurre con transición visual suave.
7. En agentes, "Configurar" abre modal con textarea editable precargada.
8. Skills muestra al menos 4 ítems con nombre, descripción y contador de uso.
9. Contrataciones muestra al menos 4 contratos y el modal de detalle incluye desglose de skills con precios individuales.
10. Log de errores muestra al menos 6 entradas con badges de severidad por color.
11. Todos los dropdowns se cierran al hacer clic fuera.
12. Todos los modales se cierran al hacer clic en el backdrop.
13. El toggle de tema cambia todo el panel entre claro/oscuro usando utilidades `dark:`.
14. La preferencia de tema persiste entre cambios de sección.
15. La implementación usa únicamente HTML + Tailwind CDN + JS vanilla, sin backend ni frameworks.