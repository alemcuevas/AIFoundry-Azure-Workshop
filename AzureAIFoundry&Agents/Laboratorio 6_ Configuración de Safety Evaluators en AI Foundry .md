# Laboratorio 6: Configuración de Safety Evaluators en AI Foundry para Andina

## Objetivo

En este laboratorio configuraremos los mecanismos de Responsible AI nativos de AI Foundry:

- Activaremos evaluadores de seguridad (Safety Evaluators)
- Validaremos la detección de inconsistencias y contenido inapropiado
- Veremos cómo AI Foundry aplica controles automáticos sobre el output de los agentes

Los Safety Evaluators son fundamentales para Andina, ya que permiten asegurar la calidad y confiabilidad de las respuestas en contextos como logística, mantenimiento, regulaciones sanitarias, y atención a clientes internos.

---

## Prerrequisitos

- Haber completado el Laboratorio 5
- Tener un agente funcional con Memories, Tools y Skills conectados (por ejemplo: agente-logistica-andina)
- Acceso al proyecto de AI Foundry en uso

---

## ¿Qué son los Safety Evaluators?

- Permiten inspeccionar y validar los resultados generados por un agente
- Operan en tiempo real mientras se ejecuta el reasoning plan
- Evalúan groundedness, toxicidad, factual consistency, riesgo de alucinaciones, y contenido sensible

---

## Paso 1 - Crear el Storage Account (si no lo tienes)

1. Ve a https://portal.azure.com  
2. Busca **Storage accounts** y haz clic en **+ Create**  
3. Llena los campos:  
   - Nombre: `andinasaieval`  
   - Tipo: `ADLS Gen2`  
   - Redundancia: `LRS`  
   - Región: la misma que tu AI Foundry  

4. Entra al recurso > crea un contenedor llamado `evals`  
5. Sube ahí el archivo `eval_set.jsonl` que usarás en el laboratorio

---

## Paso 2 - Crear el archivo `.jsonl` para pruebas

Ejemplo para el agente de stock en bodegas de Andina:

{"input": "¿Cuántas cajas de Fanta hay disponibles en Puente Alto?", "expected_output": "≈"}  
{"input": "¿Dónde se almacenan las botellas retornables de Coca-Cola 1.5L?", "expected_output": "≈"}  
{"input": "¿Qué productos están a punto de vencer en la planta de Renca?", "expected_output": "≈"}

> El símbolo `≈` indica que se usará comparación semántica

Guarda como `eval_set.jsonl` y súbelo a tu contenedor.

---

## Paso 3 - Obtener URL SAS

1. Ve a tu contenedor  
2. Haz clic en **Generate SAS**  
3. Habilita `Read` y configura una fecha de expiración  
4. Copia la URL con `?sig=...`

---

## Paso 4 - Crear la evaluación en AI Foundry

1. Ve a tu proyecto en https://ai.azure.com  
2. Accede a la sección **Evaluations**  
3. Haz clic en **+ New evaluation** y llena:  
   - Nombre: `evaluacion-stock-andina`  
   - Agent: tu agente principal  
   - Eval set source: Azure Blob Storage  
   - Método: `LLM-based` o `exact match`  
   - Pega la URL SAS

---

## Paso 5 - Crear evaluadores de seguridad

1. En la misma sección, crea evaluadores desde **Create Evaluator**
2. Selecciona `Groundedness`, `Toxicity`, o `Factual Consistency`
3. Completa los campos y guarda

---

## Paso 6 - Evaluar directamente con preguntas generadas

Esta opción es útil si aún no tienes respuestas definidas.

1. Selecciona **Evaluate model**  
2. En **Simulate Questions**, escribe el prompt para generación automática:

