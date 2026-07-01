# GRAFO DE RELACIONES — SUPER EQUIPO DE AGENTES INTERNOS

> Mapa del "grafo implícito" que ya existe en el equipo, extraído de los `[[wiki-links]]` y de los cruces escritos en cada agente. Sirve como (a) mapa visual para navegar el equipo y (b) columna de aristas lista si algún día se activa **GraphRAG** (ver `grafo_relaciones.json`).
>
> **Nota de legibilidad:** los **19 agentes citan `FILOSOFIA_TRANSVERSAL`** (es la espina dorsal del mindset). Esas 19 aristas NO se dibujan aquí para no saturar el mapa; están completas en el JSON. Abajo solo se dibujan los **cruces funcionales** (los valiosos y menos obvios).

## Mapa visual

```mermaid
graph LR
  subgraph A["ESCUADRÓN A · Ventas con IA"]
    embudo["Arquitecto de Embudo IA"]
    contact["Ingeniero de Contactabilidad"]
    redactor["Redactor Conversacional"]
    maquina["Máquina de Contenido y Clipping"]
  end

  subgraph B["ESCUADRÓN B · Impacto Social"]
    modelos["Arquitecto de Modelos Autosostenibles"]
    fundraising["Estratega de Fundraising y Acceso"]
    narrativa["Estratega de Narrativa e Incidencia"]
  end

  subgraph V["CONSTRUCCIÓN Y ESCALAMIENTO"]
    capacidad["Arquitecto de Capacidad de Ventas"]
    reclutador["Reclutador de Estrellas"]
    competitivo["Estratega Competitivo (Winner-Take-All)"]
    yc["Estratega de Fundamentos de Startup (YC)"]
  end

  subgraph M["MARKETING Y CONTENIDO"]
    reels["Estratega de Reels Virales que Venden"]
    editor["Editor y Productor de Contenido Corto"]
    creatividad["Estratega de Creatividad y Originalidad"]
  end

  subgraph T["OTROS TRANSVERSALES"]
    ventaprop["Venta con Propósito (Efecto B)"]
    prodagent["Productividad Agéntica"]
    formador["Formador y Coach de Adopción de IA"]
    mentalidad["Coach de Mentalidad de Alto Rendimiento"]
    comunicacion["Coach de Comunicación de Alto Impacto"]
  end

  ref["REFERENCIA · Modelos de Negocio Online"]

  %% --- Flujos internos de escuadrón ---
  embudo -->|flujo| contact
  embudo -->|flujo| redactor
  maquina -->|alimenta leads| embudo
  modelos -->|flujo| fundraising
  modelos -->|flujo| narrativa

  %% --- Marketing y contenido ---
  creatividad -->|alimenta ideas| reels
  creatividad -->|alimenta ideas| maquina
  reels -->|diseña, luego escala| maquina
  editor -->|produce/edita| reels

  %% --- Construcción y escalamiento ---
  reclutador <-->|coordinan| capacidad
  capacidad -->|coordina| embudo
  competitivo -->|usa como pieza| reclutador
  competitivo -->|usa como pieza| capacidad

  %% --- IA / productividad ---
  prodagent <-->|complementan| formador

  %% --- Comunicación / venta ---
  comunicacion -->|el CÓMO se dice| ventaprop

  %% --- Fundamentos YC como hub que deriva a los específicos ---
  yc -->|organización de ventas| capacidad
  yc -->|mercado / incumbente| competitivo
  yc -->|criterio vs. creencia| mentalidad
  yc -->|contratar/despedir| reclutador
  yc -->|operar: foco/métricas| prodagent
  yc -->|escuchar al usuario| modelos
  yc -->|necesidades latentes| ventaprop
  yc -->|exploración/restricciones| creatividad
  yc -->|papeleo de rondas| fundraising

  %% --- Documento de referencia ---
  ref -.->|material de consulta| modelos

  classDef doc fill:#eee,stroke:#999,stroke-dasharray:3 3;
  class ref doc;
```

## Lectura del grafo (qué revela)

- **`FILOSOFIA_TRANSVERSAL` es el nodo más conectado** (19 aristas): es el mindset común. Cualquier motor de recuperación debería tratarlo como contexto de fondo casi siempre.
- **`Estratega de Fundamentos de Startup (YC)` es el segundo hub**: se conecta con 9 agentes. Funciona como "router" — da el marco y **deriva** al agente específico según el cuello de botella (ventas, equipo, competencia, producto, fundraising, mindset, operación).
- **Dos cadenas de producción claras:** (1) *Creatividad → Reels → Editor → Máquina de Contenido* (idea → pieza → producción → escala) y (2) *Modelos → Fundraising / Narrativa* (Escuadrón B).
- **Cluster de escalamiento comercial:** *Capacidad de Ventas ↔ Reclutador*, ambos "usados como pieza" por el *Estratega Competitivo*.

## Tipos de relación (aristas)

| Tipo | Significado |
|---|---|
| `cita_filosofia` | El agente se apoya en la filosofía transversal (mindset base) |
| `flujo` | Salida de A entra como insumo directo de B (secuencia de trabajo) |
| `alimenta` | A genera insumos (ideas, leads, evidencia) para B |
| `complementa` | A y B cubren mitades distintas de un mismo problema |
| `coordina` | Trabajan en paralelo sobre el mismo objetivo |
| `usa_como_pieza` | A orquesta a B como componente de su estrategia |
| `encadena` | A deriva/pasa el trabajo a B en una secuencia |
| `referencia` | Documento de consulta (no agente) usado por un agente |

## Cómo usar esto

1. **Hoy:** como mapa mental para saber a qué agente encadenar después de otro (handoffs del manual).
2. **Mañana (si el corpus crece):** `grafo_relaciones.json` es la capa de aristas para un **GraphRAG**; combinado con búsqueda semántica sobre los `conocimiento.md`, permite consultas de "conecta los puntos" entre dominios.
3. **Mantenimiento:** cada vez que se enriquece un agente con un nuevo cruce (`> Cruce útil: ...`), agregar la arista al JSON. Es barato y mantiene el grafo vivo.
