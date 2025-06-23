# Laboratorio 3: Configuración de Memories en AI Foundry para Andina

## Objetivo

En este laboratorio aprenderemos a configurar la memoria vectorial (Knowledge) de un agente en Azure AI Foundry, utilizando exclusivamente el portal web, sin necesidad de usar código ni Visual Studio Code.

> Nota: En la versión actual de Azure AI Foundry (junio 2025), la configuración de Memories se gestiona desde la sección Knowledge dentro del agente.

---

## Prerrequisitos

- Acceso al portal de Azure AI Foundry: https://ai.azure.com/  
- Haber creado previamente:
  - Un AI Hub
  - Un Project dentro del Hub (por ejemplo: `ai-foundry-andina-lab`)
  - Un Agent dentro del Project (por ejemplo: `agente-seguridad-operacional`)

---

## Contexto de Andina

El agente que configuraremos en este laboratorio tiene como propósito asistir al personal técnico y de operaciones en Andina, brindando información sobre **protocolos de seguridad industrial**, **manuales técnicos** y **planes de mantenimiento preventivo**. Esta memoria puede contener políticas internas, manuales de fabricantes, instructivos de operación y normativa interna.

---

## Paso 1 - Ingresar al Agent

- Desde el menú lateral izquierdo, ingresar a la sección **Agents**  
- Seleccionar el agente `agente-seguridad-operacional`  
- Acceder al editor del agente

---

## Paso 2 - Acceder a la sección Knowledge

- Dentro de la pantalla de configuración del agente, localizar la sección **Knowledge**  
- Hacer clic en **+ Add** para agregar un nuevo vector store

![image](https://github.com/user-attachments/assets/9b9b1ca9-f0f6-4208-bbfb-62fb34cd2f77)  
![image](https://github.com/user-attachments/assets/33d4369b-3eb0-4962-b6f8-7eae8d580424)

---

## Paso 3 - Crear o asociar el Vector Store

- Seleccionar uno de los Vector Stores previamente configurados en el proyecto  
  (por ejemplo: Azure AI Search, Blob Storage + Embeddings, Cosmos DB vector, etc.)

- Si no existe aún, crear uno nuevo desde el menú izquierdo:  
  - Ir a **Vector Stores**  
  - Crear el recurso seleccionando:
    - Tipo de almacenamiento (recomendado: Azure AI Search)  
    - Modelo de embeddings (por ejemplo: text-embedding-ada-002)  
  - Confirmar la creación

> Recomendación: usar nombres descriptivos como `vs-seguridad-andina` o `vs-mantenimiento-fabril`

---

## Paso 4 - Cargar datos al Vector Store

- Desde la sección **Vector Stores**, seleccionar el vector store creado  
- Subir archivos de datos relevantes:  
  - Protocolos de seguridad en plantas  
  - Manuales de uso de maquinaria  
  - Checklists de mantenimiento  
  - Políticas de respuesta ante emergencias  

- El sistema realizará automáticamente el **chunking** y la **indexación semántica** de los documentos usando el modelo de embeddings seleccionado  

- Validar que los documentos aparecen como cargados correctamente

![image](https://github.com/user-attachments/assets/3f778bd8-24ae-47bd-ae34-b86781761cd1)  
![image](https://github.com/user-attachments/assets/03111f45-b7eb-4c13-8b54-1a0986cab071)  
![image](https://github.com/user-attachments/assets/4094bf6a-e569-4cac-a152-89e267b93ad6)

---

## Paso 5 - Asociar el Vector Store al agente

- Volver al agente `agente-seguridad-operacional`  
- En la sección **Knowledge**, seleccionar el vector store creado (`vs-seguridad-andina`)  
- Confirmar la asociación

---

## Paso 6 - Validación en el Playground

- Hacer clic en **Try in playground**  
- Probar preguntas que estén alineadas con el conocimiento cargado. Ejemplos:

  - ¿Cuál es el procedimiento en caso de fuga de gas en la línea de embotellado?  
  - ¿Cada cuánto se realiza mantenimiento al compresor de aire Atlas Copco?  
  - ¿Qué equipo requiere bloqueo eléctrico antes de intervenirlo?  
  - ¿Dónde se encuentran los puntos de evacuación del centro de distribución de Renca?

- Verifica si el agente utiliza correctamente la información cargada en la memoria vectorial

---

## Consideraciones adicionales

- La short-term memory (memoria de corto plazo en conversaciones) es administrada por el runtime del agente y no se puede configurar manualmente en el portal  
- Este laboratorio se enfoca en configurar long-term memory basada en documentos indexados semánticamente mediante embeddings  
- En contextos empresariales como Andina, esta funcionalidad puede utilizarse para:
  - Capacitación de nuevos técnicos  
  - Reducción de tiempo de búsqueda de información crítica  
  - Apoyo durante inspecciones o turnos nocturnos sin supervisor directo

---

## Recursos oficiales

- https://learn.microsoft.com/en-us/azure/ai-foundry/how-to-knowledge-sources  
- https://learn.microsoft.com/en-us/azure/ai-foundry/how-to-vector-stores
