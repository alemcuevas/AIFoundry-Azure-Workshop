# Laboratorio 5: Creación de Connected Skills en Azure AI Foundry para Andina

## Objetivo

En este laboratorio aprenderemos a crear y conectar agentes secundarios (Connected Skills) a un agente principal en Azure AI Foundry. Esto permite componer soluciones más modulares, delegando tareas especializadas a subagentes.

---

## Prerrequisitos

- Tener un agente principal ya creado (por ejemplo: `agente-operaciones-andina`)
- Haber creado al menos un agente adicional que actuará como skill (por ejemplo: `agente-inventario`, `agente-mantenimiento`)
- Acceso al portal de Azure AI Foundry: https://ai.azure.com/

---

## Pasos del laboratorio

### Paso 1 - Crear los agentes secundarios (skills)

- Desde la sección **Agents**, haz clic en **+ New agent**
- Asigna un nombre y propósito específico a cada agente. Ejemplos:  
  - `agente-inventario` → responde consultas sobre niveles de stock y ubicación de productos  
  - `agente-mantenimiento` → responde sobre protocolos y frecuencias de mantenimiento preventivo  

Asegúrate de asignar instrucciones claras y específicas para su dominio:

Skill: `agente-inventario`

Eres un agente especializado en gestión de inventario y stock en centros de distribución de Andina. Solo respondes preguntas relacionadas con niveles de existencias, ubicación de productos, productos agotados o próximos a vencerse.

Si el usuario consulta algo ajeno a inventario, indica que no puedes ayudar con eso.

![image](https://github.com/user-attachments/assets/7ccb8846-3cb2-4127-888c-7e876f38826d)

Ejemplos de lo que sí puedes responder:
- ¿Cuántas cajas de Sprite hay en el centro de distribución de Renca?
- ¿Qué productos están próximos a vencer?
- ¿Dónde está almacenada la presentación de Coca-Cola 1.5L?

No respondas preguntas que no tengan que ver con inventario o stock.

![image](https://github.com/user-attachments/assets/d8aec19b-a8d6-4044-8954-e98f0c1d379c)

![image](https://github.com/user-attachments/assets/9783b038-bbe6-4f90-8944-3e0c7301e8d2)

---

### Paso 2 - Acceder al agente principal

- En la sección **Agents**, selecciona tu agente principal (ejemplo: `agente-operaciones-andina`)
- Accede a su configuración

---

### Paso 3 - Agregar Connected Skills

- En el panel lateral derecho, desplázate a la sección **Connected agents (0)**
- Haz clic en **+ Add**
- Selecciona uno o más agentes que actuarán como skills
- Opcional: define un nombre personalizado para cada skill si quieres que el agente los invoque por nombre
- Guarda los cambios

![image](https://github.com/user-attachments/assets/27f38936-093b-4cb9-8825-cf6005428502)  
![image](https://github.com/user-attachments/assets/c4e48f82-efba-4c43-bfaf-b5de1c7ed511)  
![image](https://github.com/user-attachments/assets/e4db5ff5-e115-422b-9201-9ed207fd03a4)

---

### Paso 4 - Validar en el Playground

- Haz clic en **Try in playground** desde el agente principal  
- Prueba preguntas que correspondan al dominio de los skills conectados. Ejemplos:  
  - ¿Cuántos pallets hay disponibles en el centro de distribución de Puente Alto?  
  - ¿Dónde están las latas de Fanta 350ml?  
  - ¿Cuál es la frecuencia de mantenimiento del sistema de refrigeración? (si agregaste un `agente-mantenimiento`)  

El agente principal debería delegar automáticamente la tarea al skill adecuado y devolver la respuesta final.

![image](https://github.com/user-attachments/assets/55a27546-2850-44c6-a6c8-df7568977ca3)

---

## Consideraciones adicionales

- Los Connected Skills funcionan mejor cuando cada skill tiene un dominio claro y no se superponen demasiado  
- Puedes conectar múltiples skills a un solo agente, y el runtime decidirá cuál invocar según el contexto  
- En organizaciones como Andina, esta arquitectura puede reflejar áreas funcionales (logística, mantenimiento, finanzas internas, etc.)

---

## Recursos oficiales

- https://learn.microsoft.com/en-us/azure/ai-foundry/how-to-connected-agents  
- https://learn.microsoft.com/en-us/azure/ai-foundry/overview-agent-composition
