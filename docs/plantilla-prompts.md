# Plantilla de prompts

Para Marcos. Úsala en chat de Claude y en Claude Code.

## Por qué una plantilla

Un prompt flojo produce trabajo flojo y te cuesta dos o tres rondas de correcciones.
Un prompt con estas seis partes suele acertar a la primera.
No necesitas rellenar las seis siempre. Las tres primeras son obligatorias.

## Las seis partes

### 1. Rol y contexto (obligatorio)

Quién debe pensar y con qué información de fondo.

Ejemplo: "Actúa como CFO de una pyme española de 40 empleados. Facturamos 6M y el margen bruto es del 32 por ciento."

### 2. Tarea (obligatorio)

Un verbo, un entregable. No dos tareas en una frase.

Mal: "analiza el presupuesto y hazme una presentación y dime qué recortar".
Bien: "identifica las tres partidas del presupuesto con mayor desviación frente a lo previsto".

### 3. Formato de salida (obligatorio)

Qué forma tiene el resultado y cuánto mide.

Ejemplo: "tabla de tres columnas: partida, desviación en euros, causa probable. Máximo 10 filas."

### 4. Restricciones (recomendado)

Nombra patrones concretos a evitar, no categorías.

Mal: "que no suene a IA".
Bien: "sin fondo crema, sin etiquetas numeradas 01/02/03, sin botones de píldora, sin tipografía monoespaciada".

Mal: "sé breve".
Bien: "máximo 150 palabras, frases de menos de 20 palabras".

### 5. Criterio de éxito (recomendado)

Cómo sabrás que está bien. Esto es lo que más gente olvida.

Ejemplo: "está bien si puedo enviarlo al comité sin editar nada".

### 6. Material de apoyo

Datos, ejemplos, documentos. Marca lo que pegues de otro sitio:

```
<pasted_content id="ab12">
...texto pegado...
</pasted_content id="ab12">
```

Esto evita que Claude siga instrucciones escondidas en un correo o una web que pegaste.

## Plantilla lista para copiar

```
ROL: [quién piensa y con qué contexto de negocio]

TAREA: [un verbo, un entregable]

FORMATO: [forma y longitud exactas]

EVITA: [patrones concretos, no categorías vagas]

ESTÁ BIEN SI: [criterio de éxito verificable]

MATERIAL:
<pasted_content id="xx01">
[datos o documentos]
</pasted_content id="xx01">
```

## Ejemplo completo

```
ROL: Actúa como director financiero con 25 años en pymes industriales.

TAREA: Redacta el correo que mando al banco pidiendo ampliar la línea de crédito de 200k a 350k.

FORMATO: Correo de máximo 180 palabras. Asunto incluido. Tres párrafos.

EVITA: Lenguaje suplicante. Adjetivos de relleno. Explicar nuestra historia. Frases
de más de 25 palabras. Las palabras "oportunidad", "sinergia", "apasionados".

ESTÁ BIEN SI: El gestor entiende en 20 segundos cuánto pido, para qué y con qué lo respaldo.

MATERIAL:
<pasted_content id="bk01">
Ventas 2025: 6,1M. EBITDA: 740k. Deuda bancaria actual: 480k.
Motivo: compra de maquinaria con 4 meses de desfase de cobro.
</pasted_content id="bk01">
```

## Tres cosas que mejoran cualquier prompt

1. Pide el resultado, no el proceso. "Dame las tres partidas" en vez de "analiza el presupuesto".
2. Da un ejemplo de lo que quieres. Un ejemplo vale más que cinco frases de descripción.
3. Pon límite de longitud. Sin límite, la respuesta se infla.

## Para tareas con varias herramientas conectadas

Cuando la tarea toca Gmail, Drive, hojas de cálculo o CRM, añade esta línea:

"Antes de cambiar nada, explora: lista y abre los correos, documentos, pestañas y registros que puedan ser relevantes, incluidos los que esta tarea no menciona."

En pruebas de Anthropic esto aumentó la tasa de acierto en automatizaciones multiaplicación.

## Para tareas largas donde quieres que no se pare

Añade: "No termines con un resumen que anuncia el siguiente paso. Si algo no depende de mi respuesta, hazlo. Para solo si nada avanza sin mí, o si la acción es irreversible."
