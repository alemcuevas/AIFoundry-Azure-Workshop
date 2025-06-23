# Laboratorio 2: Creación del primer Agent GPT-4o en AI Foundry para Andina

## Objetivo

En este laboratorio vamos a crear el primer Agent básico utilizando GPT-4o como modelo de reasoning central.

El Agent podrá recibir prompts, ejecutar reasoning básico y entregar respuestas directamente dentro del entorno de AI Foundry.

---

## Prerrequisitos

- Haber completado el **Laboratorio 1**.
- Workspace y Project de AI Foundry ya configurados.
- Confirmación de disponibilidad del modelo `gpt-4o`.

---

## Paso 1 - Acceso al proyecto de AI Foundry

1. Inicia sesión en Azure AI Studio:  
   https://ai.azure.com

2. Navega al Workspace creado (`ws-andina-foundry`).

3. Ingresa al **Project** creado en el Lab 1 (`ai-foundry-andina-lab-#`).

---

## Paso 2 - Creación del Agent

1. Dentro del Project, selecciona **Agents** en el menú lateral.

2. Haz clic en **Create Agent**.

3. Completa los campos básicos:

- **Agent Name:**  
  `agente-andina-gpt4o-1`
- **Description (opcional):**  
  `Primer agente creado para Andina utilizando GPT-4o`
- **Objective (System Prompt):**  
  ```markdown
  Eres un agente de IA de soporte para operaciones en Andina. Respondes preguntas de forma clara, profesional, basada en datos, y enfocada en procesos industriales y logísticos. Si no tienes suficiente información, indicas que no puedes responder con certeza.
