# Requisitos del Panel de Administración — AgentHub

El panel debe incluir las siguientes seis secciones, accesibles desde una navegación lateral persistente. Un toggle en la barra superior debe permitir cambiar toda la interfaz entre modo claro y modo oscuro usando las utilidades `dark:` de Tailwind.

### 1. Dashboard
De un vistazo, el administrador debe poder ver:
* **Ingresos totales generados** (este mes).
* **Pérdida total** por descuentos y cupones.
* **Número de agentes activos** en todos los clientes.
* **Número de agentes fallando** actualmente.

> **Nota visual:** Cada uno de estos debe ser una tarjeta de métrica visible. Debajo de las tarjetas, incluye un área de marcador de posición para un gráfico de actividad semanal.

### 2. Gestión de usuarios
Una tabla que lista todos los usuarios registrados (nombre, email, plan, estado).
* Cada fila debe tener un **dropdown de acciones** — un pequeño menú activado con un botón `⋮` — con al menos dos opciones: "Ver detalle" y "Eliminar".
* Al elegir "Ver detalle" se abre un **modal overlay** con el registro completo del usuario. El modal debe cerrarse mediante un botón y haciendo clic en el backdrop (fondo oscuro).

### 3. Gestión de agentes
Un listado de todos los agentes registrados en la plataforma, mostrando nombre del agente, propietario, estado actual (activo / inactivo / fallando) y una lista de skills colapsada.
* Las skills asociadas a cada agente están ocultas por defecto; hacer clic en un control expandible las revela con una transición suave.
* Cada agente también tiene un **dropdown de acciones** con las opciones "Configurar" — que abre un modal con el prompt de sistema del agente — y "Eliminar".

### 4. Skills
Una sección dedicada al catálogo de skills disponibles — las capacidades que se pueden adjuntar a los agentes.
* Cada skill tiene un nombre, una descripción breve, y un indicador de cuántos agentes la tienen habilitada actualmente.
* Incluye una breve explicación dentro del panel sobre qué significa una "skill" en el contexto de AgentHub.
* Las skills también tienen un **dropdown de acciones** con "Ver detalle" y "Eliminar".

### 5. Contrataciones de agentes
Una tabla que muestra todos los contratos de alquiler activos y pasados.
* Cada fila debe mostrar el cliente, el agente alquilado, las skills contratadas, las fechas del contrato y el importe total pagado.
* Cada fila tiene un **dropdown de acciones**. 
* Al elegir "Ver detalle" se abre un **modal** con el desglose completo del contrato, incluyendo la lista desglosada de skills contratadas y sus precios individuales.

### 6. Log de errores
Un registro de errores de ejecución de los agentes — mostrando timestamp, nombre del agente, tipo de error y una descripción breve.
* Los errores deben categorizarse visualmente por tipo o gravedad usando **badges con código de color**.
* Cada entrada tiene un **dropdown de acciones** con "Ver detalle" (abre un modal con la traza completa del error) y "Marcar como resuelto".

---

**Consideraciones Finales**
El panel debe sentirse profesional e inmediatamente utilizable como referencia para el desarrollo futuro. Todos los datos deben estar **hardcodeados** — el equipo no espera conexiones a API ni backend en esta etapa.

**Tu trabajo es escribir la especificación primero, commitearla al repositorio, y luego construir el prototipo contra ella.**

### 💻 Qué debes hacer

**Escribe la especificación primero**
* En `SPECS.md`, escribe una especificación estructurada que incluya:
  * Una breve descripción del producto (qué es AgentHub y quién es el usuario administrador).
  * El stack tecnológico y las restricciones (HTML, Tailwind vía CDN, solo JS vanilla, sin frameworks, sin backend).
  * Al menos 3 especificaciones por sección – cada una describiendo un requisito visual o interactivo concreto para esa vista. Una buena entrada de spec nombra un componente, describe su contenido y define su comportamiento. Por ejemplo, para el Dashboard: *(1) cuatro tarjetas de métricas en una cuadrícula responsive 2x2, cada una con un icono, una etiqueta y un valor hardcodeado; (2) las tarjetas usan colores de acento distintos por tipo de métrica e incluyen una sombra sutil; (3) debajo de las tarjetas, un div de ancho completo con borde discontinuo y una etiqueta centrada representa el gráfico de actividad semanal.* Aplica este nivel de detalle a las seis secciones.
  * Un inventario de componentes: una lista de los componentes de UI reutilizables que aparecen en varias secciones (sidebar, tarjeta de métrica, dropdown de acciones, modal, badge, lista de skills colapsable, toggle de modo oscuro).
  * Criterios de aceptación: una lista numerada de condiciones verificables que deben cumplirse para que el prototipo se considere completo – incluye al menos un criterio por comportamiento interactivo (dropdown, modal, colapsable, modo oscuro).
* Usa el contenido de `SPECS.md` para generar una propuesta visual en Google Stitch y úsala como guía de diseño (no como entrega final).

> ⚠️ **IMPORTANTE:** La especificación debe estar commiteada antes del primer archivo HTML. Usa un commit separado para la spec – se revisará el historial de Git. Un agente de código IA debería poder leer tu `SPECS.md` y construir el panel desde él sin hacer ninguna pregunta. Ese es tu estándar de calidad.
> 
> ⚠️ **IMPORTANTE:** La propuesta visual de Stitch es solo un punto de partida. Debes adaptar estructura, componentes e interacciones para que coincidan exactamente con los requisitos de este proyecto.

---

**Construye el prototipo**
* Construye el panel de administración como un único archivo `index.html` (o varios archivos HTML enlazados, uno por sección).
* Usa Tailwind CSS vía CDN para todos los estilos – sin archivos CSS personalizados, sin atributos `style` en línea.
* Implementa una barra lateral (sidebar) persistente con enlaces de navegación a las seis secciones y un indicador de sección activa.

**Dashboard**
* Cuatro tarjetas de métricas (ingresos totales, pérdidas por descuentos, agentes activos, agentes fallando), cada una con un icono, una etiqueta y un valor hardcodeado.
* Un área de ancho completo debajo de las tarjetas que representa un gráfico de actividad semanal.

**Gestión de usuarios**
* Una tabla con al menos 5 filas de usuarios hardcodeados mostrando nombre, email, plan y badge de estado.
* Cada fila tiene un dropdown `⋮` con "Ver detalle" y "Eliminar".
* "Ver detalle" abre un modal con el registro completo del usuario. El modal se cierra con el botón de cierre y haciendo clic en el backdrop.

**Gestión de agentes**
* Un listado con al menos 4 agentes, cada uno mostrando nombre, propietario, badge de estado y una lista de skills colapsada.
* Hacer clic en el control expandible revela las skills del agente con una transición suave; volver a hacer clic las colapsa.
* Cada agente tiene un dropdown `⋮` con "Configurar" y "Eliminar". "Configurar" abre un modal con el prompt de sistema del agente en un `<textarea>` editable.

**Skills**
* Un catálogo de al menos 4 skills, cada una mostrando nombre, descripción y el número de agentes que la tienen habilitada.
* Una breve explicación dentro del panel sobre qué es una "skill" en el contexto de AgentHub.
* Cada skill tiene un dropdown `⋮` con "Ver detalle" y "Eliminar".

**Contrataciones de agentes**
* Una tabla con al menos 4 contratos mostrando cliente, agente, skills contratadas, fechas de inicio/fin e importe pagado.
* Cada fila tiene un dropdown `⋮`. "Ver detalle" abre un modal con el desglose completo del contrato, incluyendo skills desglosadas y sus precios individuales.

**Log de errores**
* Al menos 6 entradas de error hardcodeadas mostrando timestamp, nombre del agente, badge de tipo de error con código de color, y descripción breve.
* Cada entrada tiene un dropdown `⋮` con "Ver detalle" y "Marcar como resuelto".

**Interacciones globales**
* Un toggle de modo oscuro/claro en la barra superior cambia todo el panel entre esquemas de color usando las utilidades `dark:` de Tailwind. El modo elegido se conserva al navegar entre secciones.
* Todos los dropdowns de acciones se cierran al hacer clic fuera de su área.
* Todos los modales se cierran al hacer clic en el backdrop.

> ⚠️ **IMPORTANTE:** Toda la interactividad debe implementarse con JavaScript vanilla únicamente — sin frameworks (React, Vue, etc.), sin jQuery, sin herramientas de build. Tailwind debe cargarse solo vía CDN.