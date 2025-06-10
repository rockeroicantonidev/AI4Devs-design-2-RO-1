# Conversación principal, Chatbot: ChatGPT (o3)

## Promts
## Prompt 1. ¿que conoces acerca del Product Requirements Document (PRD)?

## Prompt 2. Eres un experto analista de negocio y tienes conocimientos amplios en levantamiento de requerimientos. A continuación te adjunto un documento que es el análisis previo de producto para desarrollar un Applicant Tracking System (ATS). Tu tarea es organizar esta información para convertirla en un Product Requirements Document (PRD). El objetivo es tener un documento formal del cual partir para trabajar con las partes interesadas y el equipo de desarrollo. El contenido es para el publico en general. Tus pautas para generar el contenido son:
1. Omitas crear o incluir historias de usuario, eso se realizara mas adelante.
2. Omitas incluir requisitos técnicos.
3. Omitas incluir criterios de aceptación, eso se realizara mas adelante.
Realiza preguntas si requieres mas información.
[Documento Adjunto del ejercicio anterior]

## Prompt 3. Ahora tienes el rol de analista de negocio y product owner. Tu tarea es generar las historias de usuario mínimas para un MVP a partir del PRD generado.
Utiliza la siguiente plantilla
--- PLANTILLA ---
## 1. Identificador Único  
[Código único de referencia]  

---

## 2. Título  
[Nombre descriptivo y conciso de la funcionalidad]  

---

## 3. Descripción  
*Como [rol o tipo de usuario], quiero [acción u objetivo] para [beneficio o valor].*  

---

## 4. Criterios de Aceptación  
### Escenario: [Nombre del caso de prueba]  
**Dado que** [condición inicial o contexto]  
**Cuando** [acción realizada por usuario/sistema]  
**Entonces** [resultado observable]  
**Y** [resultado adicional opcional]  

*(Repetir estructura para cada escenario necesario)*  

---

## 5. Detalles Adicionales (Opcionales)  
**Prioridad:** [Alta/Media/Baja]  
**Dependencias:** [IDs de historias relacionadas]  
**Notas Técnicas:** [Requisitos técnicos especiales]  
**Diseño:** [Enlace o referencia a recursos visuales]  
**Métricas:** [Criterios de éxito medibles]  

---

## 6. Validación  
- [ ] Descripción cumple formato "Como... quiero... para..."  
- [ ] Criterios cubren todos los caminos críticos  
- [ ] Redacción comprensible para usuarios no técnicos  
*(Se espera se incluyan otras validaciones si es necesario)*  
--- FIN PLANTILLA ---
Utiliza el formato Markdown como pauta para generar el contenido.

## Prompt 4. Convierte la información generada al formato Markdown para archivos .md

## Prompt 5. Ahora eres un project manager experimentado. Utilizando la metodología MoSCoW prioriza las historias de usuario, por lo que ahora el campo de "Prioridad" tendrá el valor que la metodología ofrece. El objetivo es crear un Backlog de trabajo para el equipo de desarollo. El contenido es para el publico en general. Tus pautas para generar el contenido son:
1. Muestra el resultado en forma de lista
2. Cada elemento de la lista incluye el Id, el titulo de la historia de usuario y el valor de prioridad.
3. Presenta el contenido en formato Markdown para archivos .md

## Prompt 6. Ahora eres un project manager experimentado. Utilizando la metodología "Value vs. Effort" prioriza las historias de usuario, por lo que ahora el campo de "Prioridad" tendrá el valor que la metodología ofrece. El objetivo es crear un Backlog de trabajo para el equipo de desarollo. El contenido es para el publico en general. Tus pautas para generar el contenido son:
1. Muestra el resultado en forma de matriz, tal y como la metodología mencionada establece. 
2. Cada elemento de la lista incluye el Id, el titulo de la historia de usuario y el valor de prioridad.
3. Presenta el contenido en formato Markdown para archivos .md

## Prompt 7. A continuación requiero establecer los tickets de trabajo para la historia de usuario "ATS-US-01". Basado en la información de la historia de usuario crea las tareas que se necesitan para completar la historia de usuario, contemplando las siguientes categorías de tareas:
1. Investigación
2. Features o caracteristicas
3. Tareas Técnicas
4. Posibles mejoras.
Utiliza la siguiente plantilla para crear cada uno de los tickets.
--- PLANTILLA ---
# Plantilla para Tickets de Trabajo

## Título
`[Nombre breve y descriptivo de la tarea]`

## Descripción
`[Explicación detallada de la funcionalidad o problema]`

## Criterios de Aceptación
- `[Requisito 1]`
- `[Requisito 2]`
- `[Requisito 3]`

## Prioridad
`[Alta/Media/Baja/Crítica]`

## Asignado a
`[Equipo o persona responsable]`

## Etiquetas
`[Categoría 1]`, `[Categoría 2]`, `[Sprint/Iteración]`

## Comentarios
`[Notas adicionales o consideraciones especiales]`

## Enlaces
`[Documentación relacionada]`, `[Recursos externos]`

## Historial de Cambios
- `[Fecha]`: `[Modificación]` por `[Responsable]`
- `[Fecha]`: `[Modificación]` por `[Responsable]`
--- FIN PLANTILLA ---

--- INFORMACIÓN ADICIONAL ---
1. No existe algun desing system, debemos contemplar una tarea que realice esta definición, designa el equipo que deberá llevarla ejecutarla.
2. Por el momento se utiliza una misma base de datos, el sistema no esta orientado a microservicios.
--- FIN INFORMACIÓN ADICIONAL ---
Tus pautas para generar el contenido son:
1. Por el momento omite la estimación, eso lo realizaremos mas adelante.
2. El formato de salida es Markdown para archivos .md
3. El contenido de cada tarea utiliza la plantilla ya descrita.
¿tienes alguna pregunta sobre la tarea que vas a realizar?

### Preguntas del Chatbot
¡Antes de elaborar los tickets me gustaría confirmar un par de detalles para asegurar que el desglose sea realmente útil para tu equipo!

    Alcance de QA y documentación

        ¿Deseas que incluya tareas específicas para QA (plan de pruebas, casos manuales) y para documentación (guía de usuario interna), o esas actividades se gestionan en otro flujo?

    Separación Front-end / Back-end

        ¿Prefieres que las tareas técnicas se dividan explícitamente por stack (por ejemplo, “API CRUD de etapas” y “Componente Vue de lista/drag-and-drop”), o tu equipo combina ambos en una sola tarjeta de desarrollo?

    Lineamientos visuales

        No hay Design System actualmente; ¿existen brand guidelines (colores, tipografías) que debamos considerar al proponer la tarea de “Definir Design System básico”, o partimos completamente desde cero?

¡Con estas aclaraciones podré armar un backlog muy alineado a tus necesidades!

## Prompt 8. 1. Si incluye actividades de QA y documentación
2. dividir explicitamente por stack
3. se parte completamente desde cero

## Prompt 9. Como project manager utiliza la metodología "T-Shirt Sizing" para estimar el esfuerzo de los tickets generados para la historia de usuario "ATS-US-01", esto expresado en horas. El objetivo es obtener la estimación de cada tarea realizada. El contenido es para el equipo de desarrollo.
Tus pautas para generar el contenido son:
1. Se represente en formato de tabla con las siguientes columnas: Numero de ticket, titulo, talla, equivalencia en horas
2. El formato de salida es Markdown para archivos .md

## Prompt 10. Genera un resumen de las tareas realizadas hasta el momento.

# Conversación secundaria, Chatbot: Deep Seek (R1)

## Promtps

## 1. Eres un experto analista de negocio y project manager. Genera una plantilla para historias de usuario y criterios de aceptación. El objetivo es tener un plantilla reutilizable para historias de usuario. El contenido es para el publico en general. Tus pautas para generar el contenido es que la plantilla sea reutilizable.

## 2. Ahora sola dame la plantilla como si fuera un formulario a rellenar y sin ejemplos. El formato de salida es markdown.

## 3. ¿Que metodologias sugieres para priorizar historias de usuario? Dame al menos 5 e incluye ejemplos de uso.

## 4. De la siguiente información de ejemplo genera una plantilla para tickets de trabajo.
--- EJEMPLO ---
Título: Implementación de Autenticación de Dos Factores (2FA)

Descripción: Añadir autenticación de dos factores para mejorar la seguridad del login de usuarios. Debe soportar aplicaciones de autenticación como Authenticator y mensajes SMS.

Criterios de Aceptación:

    Los usuarios pueden seleccionar 2FA desde su perfil.
    Soporte para Google Authenticator y SMS.
    Los usuarios deben confirmar el dispositivo 2FA durante la configuración.

Prioridad: Alta

Estimación: 8 puntos de historia

Asignado a: Equipo de Backend

Etiquetas: Seguridad, Backend, Sprint 10

Comentarios: Verificar la compatibilidad con la base de usuarios internacionales para el envío de SMS.

Enlaces: Documento de Especificación de Requerimientos de Seguridad

Historial de Cambios:

    01/10/2023: Creado por [nombre]
    05/10/2023: Prioridad actualizada a Alta por [nombre]

--- FIN EJEMPLO ---
 El formato de salida es markdown para archivos .md

 ## 5. ¿Que metodologias sugieres para priorizar y estimar esfuerzo en los tickets de trabajo de una historia de usuario? Dame al menos 5 e incluye ejemplos de uso.

 