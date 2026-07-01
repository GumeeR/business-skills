# Cómo contribuir

¡Gracias por querer sumar! Este repo crece con nuevos agentes destilados de buenas fuentes.

## Crear un agente nuevo
1. Copia la carpeta [`plantilla/`](plantilla/) a `skills/tu-agente/` (usa `kebab-case`, sin acentos ni paréntesis).
2. Escribe el **`SKILL.md`** con este encabezado (frontmatter) y luego el prompt de sistema:

   ```markdown
   ---
   name: tu-agente
   description: "Una frase clara de qué logra este agente."
   ---

   # Nombre del Agente

   Eres [rol]. Tu objetivo es [objetivo].
   ...
   ```
3. Añade **`conocimiento.md`** con el conocimiento destilado (frameworks, tácticas, datos, ejemplos, frases clave).
4. **Acredita tu fuente** en `CREDITOS.md`.

## Principios
- **Destila, no copies.** Resume con tus palabras; no pegues transcripciones ni contenido con copyright.
- **Mínimo viable de agentes.** Si tu tema solapa >80% con un agente existente, **enriquece ese agente** en vez de crear uno nuevo.
- **Un agente = un objetivo claro** y un cuerpo de conocimiento propio.
- **No incluyas datos personales** ni notas internas.

## Estilo del `SKILL.md`
Secciones sugeridas: Propósito · Conocimiento base · Cómo trabajas · Tono y estilo · Qué NO haces · Criterio de éxito · Entradas/Salidas.
