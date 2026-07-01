# CONOCIMIENTO — ESTRATEGA DE GROWTH Y EXPERIMENTACIÓN

## Principios base
1. **Empieza con una hipótesis** (no "a ver qué pasa"): una predicción específica basada en dato o razonamiento.
2. **Prueba UNA cosa** por test (una variable); si no, no sabes qué funcionó.
3. **Rigor estadístico:** pre-fija el tamaño de muestra, **no espíes ni pares antes**, comprométete con la metodología.
4. **Mide lo que importa:** una métrica **primaria** ligada al valor de negocio, **secundarias** para contexto, **guardrail** para evitar daño.

## Framework de hipótesis
> *Porque [observación/dato], creemos que [cambio] causará [resultado esperado] para [audiencia]. Lo sabremos cuando [métrica].*
- **Débil:** "cambiar el color del botón quizá suba los clics".
- **Fuerte:** "Porque los usuarios reportan que no encuentran el CTA (heatmaps + feedback), creemos que un botón más grande y con color de contraste subirá los clics al CTA +15% en visitantes nuevos. Mediremos el CTR de vista de página → inicio de registro."

## Métricas: primaria / secundarias / guardrail
- **Primaria:** la única que más importa, atada a la hipótesis; es con la que "cantas" el test.
- **Secundarias:** explican por qué/cómo funcionó el cambio.
- **Guardrail:** cosas que NO deben empeorar; si se ponen muy negativas, se para el test.
- Ej. test de página de precios → Primaria: tasa de selección de plan · Secundarias: tiempo en página, distribución de planes · Guardrail: tickets de soporte, tasa de reembolso.

## Tipos de test y tráfico
| Tipo | Descripción | Tráfico |
|---|---|---|
| A/B | Dos versiones, un cambio | Moderado |
| A/B/n | Varias variantes | Alto |
| MVT | Varios cambios combinados | Muy alto |
| Split URL | URLs distintas por variante | Moderado |

- **Asignación de tráfico:** 50/50 por defecto; 90/10–80/20 para limitar riesgo; ramping (empezar chico y subir) para riesgo técnico. Consistencia: el usuario ve la misma variante al volver.

## Tamaño de muestra (referencia rápida, por variante)
| Tasa base | +10% lift | +20% lift | +50% lift |
|---|---|---|---|
| 1% | 150k | 39k | 6k |
| 3% | 47k | 12k | 2k |
| 5% | 27k | 7k | 1,2k |
| 10% | 12k | 3k | 550 |

- Calculadoras: Evan Miller (`evanmiller.org/ab-testing/sample-size.html`), Optimizely, VWO, abtestguide.
- **El problema de "espiar" (peeking):** mirar resultados antes de alcanzar la muestra y parar temprano → **falsos positivos**. Pre-comprométete a la muestra y confía en el proceso.

## Analizar resultados
- **Significancia:** 95% de confianza = p < 0,05 (<5% de que el resultado sea azar); es un umbral, no una garantía.
- **Checklist:** ¿alcanzó la muestra? ¿es significativo (intervalos de confianza)? ¿el tamaño de efecto es relevante? ¿las secundarias acompañan? ¿algún guardrail empeoró? ¿diferencias por segmento (móvil/desktop, nuevo/recurrente)?
- **Lectura:** ganador significativo → implementa · perdedor significativo → conserva el control y aprende por qué · sin diferencia → más tráfico o test más audaz · señales mixtas → segmenta y profundiza.

## Programa de experimentación (el activo compuesto)
Un test suelto vale; un **programa continuo** es un activo que compone. **El bucle:**
1. Generar hipótesis (analytics, research de clientes, competidores, tickets, heatmaps, tests pasados).
2. Priorizar con **ICE**.
3. Diseñar y correr.
4. Analizar con rigor.
5. **Promover ganadores a un playbook.**
6. Generar nuevas hipótesis desde el aprendizaje → repetir.

### Priorización ICE
Puntúa 1–10 en: **Impacto** (¿cuánto mueve la métrica si funciona?), **Confianza** (¿qué tan seguros, por dato no corazonada?), **Facilidad** (¿qué tan rápido/barato de enviar y medir?). **ICE = (I + C + E) / 3.** Corre primero lo más alto; re-puntúa mensual.

### Velocidad de experimentos (indicador adelantado de crecimiento)
- Experimentos lanzados/mes: **4–8** para la mayoría.
- Win rate: **20–30%** (uno demasiado alto = hipótesis conservadoras).
- Duración media: 2–4 semanas · Backlog: **20+** hipótesis en cola · Lift acumulado: ganancia compuesta de todos los ganadores.

### Plantilla de playbook (documentar cada ganador)
Nombre · fecha · hipótesis · tamaño de muestra · resultado (ganador/perdedor, cambio de la métrica, IC 95%, p) · guardrails · deltas por segmento · por qué funcionó/falló · **patrón reutilizable** (ej. "prueba social junto al CTA de precios sube la selección de plan") · dónde aplicarlo · estado.

## Cadencia
- **Semanal (30 min):** revisar tests activos por problemas técnicos y guardrails; no cantar ganadores antes, pero sí parar los que empeoran guardrails.
- **Quincenal:** concluir los terminados, actualizar el playbook, lanzar el siguiente del backlog.
- **Mensual (1 h):** revisar velocidad, win rate y lift acumulado; reponer backlog; re-priorizar con ICE.
- **Trimestral:** auditar el playbook (qué patrones se escalaron, qué zonas del embudo están poco testeadas).

## Errores comunes
- **Diseño:** cambio demasiado pequeño (indetectable); probar muchas cosas a la vez (no aíslas); sin hipótesis clara.
- **Ejecución:** parar antes; cambiar cosas a mitad; no verificar la implementación/tracking.
- **Análisis:** ignorar intervalos de confianza; cherry-picking de segmentos; sobre-interpretar resultados no concluyentes.

## Adaptación a este equipo
- Este método aplica a **cualquier** decisión medible (landing, oferta, guion de reel, secuencia de correo), no solo SaaS. Si el volumen es bajo (poco tráfico), prioriza cambios **audaces** (lift grande necesita menos muestra) y usa la lógica cualitativa de la Clase 15 de YC ("hablar con usuarios") como complemento.

## Fuente
Skills `ab-testing` / `ab-test-setup` + `analytics` de la biblioteca de Corey Haines (`github.com/coreyhaines31/marketingskills`, MIT), vía skillrepo.dev. Junio 2026.
Relacionado: [[filosofia-transversal]]; ver `REFERENCIA_Marketing_Skills.md`. Complementa a **Arquitecto de Embudo IA** (qué optimizar), **Estratega de Reels / Máquina de Contenido** (qué variantes probar) y la Clase 15 de YC del **Estratega de Fundamentos de Startup** (validación cualitativa).
