
# 🧠 Laboratorio-Reto: Construcción de un Agente Financiero Multicomponente para Andina en Azure AI Foundry

## 🎯 Objetivo del reto

Construir un **Agente Financiero Maestro** en Azure AI Foundry que ayude a Andina a responder preguntas clave sobre costos, márgenes, logística y proyecciones financieras, integrando múltiples agentes especializados conectados mediante **Connected Skills**.

El agente que responda con mayor precisión, claridad y valor para la operación de Andina será el ganador.

---

## 🧩 Estructura del ejercicio

Cada equipo debe construir:

1. **Agentes especializados** (mínimo 2, idealmente 4):

   - `agente_costos_insumos`: Responde preguntas sobre costos de azúcar, PET, aluminio, agua, etc.
   - `agente_logistica_rutas`: Especialista en eficiencia logística, costos por kilómetro, zonas de entrega.
   - `agente_margen_sku`: Calcula margen por presentación o SKU, considerando precios y costos actuales.
   - `agente_proyecciones_financieras`: Realiza estimaciones de ingresos, utilidades o gastos a futuro.

2. **Un agente maestro**: `agente_finanzas_andina` que actúe como orquestador y delegue inteligentemente a los agentes especializados.

---

## 🛠️ Herramientas permitidas

✅ Solo el portal de **Azure AI Foundry**:

- Prompts (Instructions)
- Connected Skills
- Tools configurados en Actions (opcional)
- Knowledge (Memories, opcional)

🚫 No se permite:

- Código externo (VSCode o SDK)
- JSON externos
- Modificaciones vía API

---

## 📝 Actividades del laboratorio

### Paso 1 – Crear los subagentes

Ejemplos:

- **`agente_costos_insumos`**  
  Instructions:
  *Eres un experto en costos de insumos como PET, azúcar, aluminio y agua. Solo respondes sobre precios, tendencias y comparativos de costos de estos materiales.*

- **`agente_logistica_rutas`**  
  Instructions:
  *Especialista en distribución y logística. Respondes sobre rutas óptimas, costos de transporte, tiempos de entrega y eficiencia logística por región.*

- **`agente_margen_sku`**  
  Instructions:
  *Calculas márgenes por SKU considerando costos directos e indirectos, precios por presentación y regiones.*

- **`agente_proyecciones_financieras`**  
  Instructions:
  *Proyectas ingresos, egresos y margen EBITDA a futuro con base en datos históricos y crecimiento esperado por canal.*

---

### Paso 2 – Crear el agente maestro

Crea `agente_finanzas_andina`.

Instructions sugeridas:

*Eres un asesor financiero para Andina. Cuando recibes una pregunta especializada, decides cuál de tus agentes expertos debe responder. Conectas múltiples subagentes para generar respuestas precisas y útiles para la toma de decisiones empresariales.*

Conecta todos los subagentes como **Connected Skills**.

---

### Paso 3 – Validar en el Playground

Usa el Playground para probar con estas preguntas:

1. ¿Cuánto costó el PET en promedio durante el último trimestre?
2. ¿Cuál es el margen estimado de la presentación de 1.5L en canal tradicional?
3. ¿Qué ruta de entrega tuvo mayor costo logístico en junio?
4. ¿Cuánto crecería el EBITDA si aumentamos ventas un 5% en supermercados?

---

## 🏆 Criterios de evaluación

| Criterio                                       | Peso |
|------------------------------------------------|------|
| Relevancia y utilidad para decisiones en Andina | 40% |
| Uso correcto y eficiente de los subagentes      | 30% |
| Calidad del prompt maestro                      | 20% |
| Especialización y claridad de los subagentes    | 10% |

---

## 🏁 Entregable

- `agente_finanzas_andina` configurado y funcional
- Al menos 2 subagentes conectados correctamente
- Captura del Playground con respuestas a las 4 preguntas
- Nombre del equipo o persona participante

---

## 📚 Recursos útiles

- [Connected Agents - Microsoft Learn](https://learn.microsoft.com/en-us/azure/ai-foundry/how-to-connected-agents)
- [Prompt Design en AI Foundry](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/prompts)
