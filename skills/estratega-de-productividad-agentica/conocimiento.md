# CONOCIMIENTO — ESTRATEGA DE PRODUCTIVIDAD AGÉNTICA

## Frameworks / Marcos mentales
- Regla de las dos veces: tarea que se repite 2+ → agente.
- Pensar en modo agéntico desde el inicio (cómo lo haría un agente, no a mano).
- La IA imita al cerebro: mínimo esfuerzo, ahorrar energía → dale contexto.
- Mentalidad de escala: piensas chiquito → pides chiquito → obtienes chiquito.

## Tácticas y métodos
- Estandarizar al equipo entrenando UN agente con tu contexto/criterio, en vez de repetir instrucciones.
- Crear el agente aunque dudes: costo casi nulo, solo consume al usarse.
- Agente coordinador cuando orquestas varios para una tarea.
- Convertir tu criterio en infraestructura reutilizable.

## Datos duros / Cifras (caso Cintia Sánchez)
- >100 agentes personales; ~12 principales; 1 orquestador encima.
- 5 agentes por empleado en su organización.
- IA como campo: existe desde ~1950 (machine learning de hace décadas); lo nuevo son las capacidades generativas.

## Frases clave / Ejemplos
- "Si una tarea la vas a hacer dos veces, se va de agente."
- "Quien entrena al agente soy yo: me parece más fácil entrenar una vez que repetirle a todos mis reportes."
- "Si piensas chiquito, tus prompts son chiquitos; solo usas el 1% de lo que puedes hacer."

## Antipatrones
- Repetir tareas a mano o repetir instrucciones al equipo en lugar de crear un agente.
- Usar la IA solo para microtareas (correo, Excel) sin visión de escala.

## Ampliación — "El contexto es todo lo que necesitas" (Sachin, Skyvern)
> Caso: Skyvern (open source, automatiza tareas en el navegador para salud) llegó a **$2M de run rate** con **un solo humano** (PM + marketing + ventas + soporte) apalancado en agentes que escriben PRDs, hacen SEO, marketing de contenido, soporte y arreglan bugs pequeños.

### La tesis central
- Los agentes producen **"slop"** no porque no sigan instrucciones, sino porque **les falta contexto**. Es como un empleado nuevo: quiere ayudar pero no conoce tu negocio → necesita **onboarding**. La receta: **buenas instrucciones + buen contexto + dejar que critiquen su propio trabajo**.
- **Buen contexto = todo sobre tu negocio:** email, Slack, Notion/documentación, **grabaciones de llamadas con clientes**, incluso acceso a la **base de datos** (para diagnosticar "este cliente hizo estas corridas y fallaron así").
- **Ventaja injusta de las empresas remotas:** el contexto queda **grabado** (llamadas, mensajes); en presencial se **habla y se pierde**. Regla: **todas tus herramientas son la base de conocimiento de la empresa; lo que no se registra, no se guarda** → reestructura la empresa para capturarlo.

### Patrón de skill de calidad (cómo evitar el slop)
1. **Recolecta evidencia** primero: el agente busca en grabaciones, Slack, Notion y comunicaciones del cliente sobre el tema.
2. **Primer borrador conciso y aterrizado en evidencia** (con enlaces a las grabaciones/fuentes concretas para quien ejecute).
3. **Revisión adversarial con sub-agentes** (que critiquen y lean los comentarios del documento).
4. **Marco de priorización** (ej. **RICE**) para **quitar los requisitos basura** que parecían importantes.
5. **Itera hasta que el equipo deje de decir "esto es slop"** (afinado con feedback real).
- Instrucciones **deliberadamente algo vagas** para dar libertad al agente en el "cómo".

### Ejemplos concretos
- **Skill "Escribe un PRD":** busca en todas las grabaciones el tema, cruza Slack/Notion/cliente, redacta, pasa por revisión adversarial y por RICE. (Ej.: problema de CAPTCHA solver → encontró las grabaciones específicas de los clientes que se quejaron y las enlazó.)
- **Skill "Marketing de contenido":** cada mañana un email con **5 ideas de post** sacadas de las **últimas 20 llamadas** (internas y externas); agrupa temas (dolores recurrentes, observaciones contrarian, lo que funciona en redes), redacta 5 posts (Twitter/LinkedIn), pasa un "AI advisor" que quita palabras sloppy, mete un meme, y lo manda a revisar → publicar **5×/semana**. (Un post autogenerado desde un requisito real de cliente le trajo un lead cualificado.)

### Reestructurar la empresa para alimentar a los agentes
- **Prohibir los DMs:** todo se pregunta en el **canal de oficina** (así cada futura contratación hereda el contexto).
- **Grabar todas las llamadas**, internas y externas (incluso los 1:1 con el cofundador).
- **Dar a los agentes acceso a todo** y **dar a todos acceso a un agente** (a los nuevos vendedores les impusieron grabar sus llamadas: incómodo la primera hora, luego se acostumbran).

## Ampliación 2 — Técnicas de proceso para construir/orquestar agentes (skills de Matt Pocock)
> Repo "Skills for Real Engineers": lo específico de código (TDD, bugs, arquitectura) NO aplica a este equipo; sí aplican estas técnicas **meta** de cómo alinear y encadenar agentes. Filosofía base que valida nuestro diseño: **skills pequeñas, adaptables y componibles, que funcionan con cualquier modelo** (un agente por dominio, mínimo viable).

### 1. Grilling — "interrógame antes de construir"
- Antes de ejecutar, el agente debe **interrogar sin piedad** hasta llegar a un entendimiento compartido: recorre **cada rama del árbol de decisiones**, resolviendo dependencias **una por una**.
- **Reglas de oro:** una **sola pregunta a la vez** (varias juntas aturden); para cada pregunta el agente **propone su respuesta recomendada**; y si algo se puede resolver **explorando el material** (grabaciones, docs, base de conocimiento) en vez de preguntar, que lo explore. Úsalo **cada vez** que vayas a hacer un cambio o pieza importante. (Es la versión operativa de "definir el porqué" y de la Clase 15 de YC: hablar antes de construir.)

### 2. Lenguaje compartido (CONTEXT.md) — el antídoto al "slop"
- Crea un **glosario/documento de dominio** del proyecto para que el agente **decodifique la jerga**. Beneficios: menos verbosidad, **nombres consistentes** en todo, el agente **gasta menos tokens pensando** y navega mejor. Ej.: decir "**la cascada de materialización**" en vez de un párrafo entero describiéndola.
- Es la **implementación concreta** del principio "el contexto es todo lo que necesitas": no solo darle datos, sino **un lenguaje común** destilado. (En este equipo, el rol de `CONTEXT.md` lo cumplen los `conocimiento.md` + `FILOSOFIA_TRANSVERSAL` + el glosario de cada dominio.)

### 3. Handoff — el traspaso entre agentes (nuestra Fase 4 de orquestación)
- Al terminar, **compacta la conversación en un documento de traspaso** para que **otro agente continúe** sin perder contexto. Reglas: incluye una sección de **"agentes/skills sugeridos"** a invocar después; **no dupliques** lo que ya vive en otros artefactos (PRDs, planes, decisiones) → **referéncialos por ruta/URL**; **redacta/omite** info sensible (claves, datos personales); y **adáptalo a en qué se enfocará la siguiente sesión**.
- Esto es exactamente el **handoff manual** del manual del equipo (copiar la salida de un agente y pegarla en el siguiente): conviene estandarizar ese "documento de traspaso" como formato fijo.

### Distinción útil para estructurar agentes
- **Invocados por el usuario** (tú los llamas; su trabajo es **orquestar**) vs. **invocados por el modelo** (los alcanza el agente solo cuando encaja; guardan la **disciplina reutilizable**). Un skill de orquestación puede llamar a varios de disciplina, pero **no** a otro de orquestación. Traducción a este equipo: el **Orquestador** (tú + este agente) invoca; los agentes de dominio guardan la disciplina.

## Fuente
Podcast 30x con Cintia Sánchez (CIO / IA para ejecutivos). Junio 2026.
Ampliación 1: charla de Sachin (Skyvern), "El contexto es todo lo que necesitas / stop the slop shop". Junio 2026.
Ampliación 2: repo `mattpocock/skills` ("Skills for Real Engineers") — técnicas transferibles: grilling, lenguaje compartido/CONTEXT.md, handoff. Junio 2026.
Relacionado: [[filosofia-transversal]]; complementa al Formador y Coach de Adopción de IA.
