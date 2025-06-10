# Historias de Usuario – MVP Applicant Tracking System (ATS)

---

## 1. Identificador Único  
`ATS-US-01`  

---

## 2. Título  
`Configurar etapas del flujo de reclutamiento`  

---

## 3. Descripción  
*Como **Administrador de RR. HH.**, quiero **definir y ordenar las etapas del proceso de reclutamiento** para **adaptar el ATS a la forma de trabajo de mi organización**.*  

---

## 4. Criterios de Aceptación  
### Escenario: Crear flujo de etapas  
**Dado que** el Administrador accede al módulo de Configuración  
**Cuando** agrega una nueva etapa con nombre y posición  
**Entonces** la etapa aparece en la lista de etapas activas  
**Y** se guarda el orden actualizado del flujo  

### Escenario: Editar nombre de etapa  
**Dado que** existe una etapa llamada “Entrevista técnica”  
**Cuando** el Administrador cambia el nombre a “Entrevista técnica 1”  
**Entonces** el nuevo nombre se refleja en todas las vacantes asociadas  

### Escenario: Eliminar etapa sin candidatos activos  
**Dado que** la etapa “Oferta” no contiene candidatos en proceso  
**Cuando** el Administrador elimina la etapa  
**Entonces** la etapa desaparece del flujo  
**Y** no afecta registros históricos  

---

## 5. Detalles Adicionales (Opcionales)  
**Prioridad:** `Alta`  
**Dependencias:** `—`  
**Notas Técnicas:** `—`  
**Diseño:** `Wireframe-Flujo-Etapas-v1`  
**Métricas:** `% de vacantes con flujo configurado = 100 % para nuevos clientes`  

---

## 6. Validación  
- [ ] Descripción cumple formato "Como... quiero... para..."  
- [ ] Criterios cubren creación, edición y eliminación  
- [ ] Redacción comprensible para usuarios no técnicos  

---

---

## 1. Identificador Único  
`ATS-US-02`  

---

## 2. Título  
`Crear vacante`  

---

## 3. Descripción  
*Como **Reclutador**, quiero **crear una nueva vacante con sus campos principales** para **publicarla y comenzar a recibir candidatos**.*  

---

## 4. Criterios de Aceptación  
### Escenario: Registro mínimo de vacante  
**Dado que** el Reclutador está en la página “Nueva vacante”  
**Cuando** completa título, ubicación y descripción obligatoria  
**Entonces** el sistema guarda la vacante en estado “Borrador”  

### Escenario: Selección de flujo de etapas  
**Dado que** hay flujos configurados (ATS-US-01)  
**Cuando** el Reclutador elige un flujo para la vacante  
**Entonces** el flujo queda asociado y visible en la pantalla de detalle  

---

## 5. Detalles Adicionales (Opcionales)  
**Prioridad:** `Alta`  
**Dependencias:** `ATS-US-01`  
**Notas Técnicas:** `—`  
**Diseño:** `Mockup-Crear-Vacante-v1`  
**Métricas:** `Tiempo promedio para crear vacante < 2 min`  

---

## 6. Validación  
- [ ] Descripción en formato correcto  
- [ ] Criterios cubren creación y asignación de flujo  
- [ ] Lenguaje claro para no técnicos  

---

---

## 1. Identificador Único  
`ATS-US-03`  

---

## 2. Título  
`Publicar vacante en portal externo`  

---

## 3. Descripción  
*Como **Reclutador**, quiero **publicar la vacante en LinkedIn/Indeed desde el ATS** para **aumentar la visibilidad y atraer candidatos rápidamente**.*  

---

## 4. Criterios de Aceptación  
### Escenario: Publicación exitosa  
**Dado que** la vacante está en estado “Borrador” y cuenta con todos los campos obligatorios  
**Cuando** el Reclutador pulsa “Publicar” y selecciona LinkedIn  
**Entonces** la vacante cambia a estado “Publicada”  
**Y** aparece el enlace de la oferta en LinkedIn  

### Escenario: Error de credenciales  
**Dado que** las credenciales API de LinkedIn son inválidas  
**Cuando** el Reclutador intenta publicar  
**Entonces** el sistema muestra mensaje de “Credenciales inválidas”  
**Y** la vacante permanece en estado “Borrador”  

---

## 5. Detalles Adicionales (Opcionales)  
**Prioridad:** `Alta`  
**Dependencias:** `ATS-US-02`  
**Notas Técnicas:** `Usar API v2 LinkedIn Jobs`  
**Diseño:** `—`  
**Métricas:** `% de publicaciones que retornan 200 OK ≥ 95 %`  

---

## 6. Validación  
- [ ] Cumple formato  
- [ ] Escenarios cubren éxito y error  
- [ ] Comprensible para no técnicos  

---

---

## 1. Identificador Único  
`ATS-US-04`  

---

## 2. Título  
`Recepción automática de candidatos`  

---

## 3. Descripción  
*Como **Sistema**, quiero **importar automáticamente las solicitudes recibidas en los portales y por correo** para **centralizar todos los candidatos en un solo listado**.*  

---

## 4. Criterios de Aceptación  
### Escenario: Importación desde LinkedIn  
**Dado que** existe una vacante publicada en LinkedIn (ATS-US-03)  
**Cuando** un candidato aplica en LinkedIn  
**Entonces** el candidato aparece en la lista de candidatos del ATS en la etapa inicial “Aplicado”  

### Escenario: Importación desde correo  
**Dado que** hay una dirección catch-all configurada  
**Cuando** un correo con CV adjunto llega a la bandeja  
**Entonces** el sistema crea un registro de candidato  
**Y** adjunta el CV al perfil  

---

## 5. Detalles Adicionales (Opcionales)  
**Prioridad:** `Alta`  
**Dependencias:** `ATS-US-03`  
**Notas Técnicas:** `Webhook LinkedIn + parser de correo IMAP`  
**Diseño:** `Diagrama-Flujo-Importacion`  
**Métricas:** `Retraso ≤ 5 min entre aplicación y registro`  

---

## 6. Validación  
- [ ] Formato correcto  
- [ ] Escenarios cubren portales y correo  
- [ ] Redacción clara  

---

---

## 1. Identificador Único  
`ATS-US-05`  

---

## 2. Título  
`Visualizar listado de candidatos centralizado`  

---

## 3. Descripción  
*Como **Reclutador**, quiero **ver un listado unificado de todos los candidatos de una vacante** para **filtrarlos y priorizar acciones**.*  

---

## 4. Criterios de Aceptación  
### Escenario: Filtro por etapa  
**Dado que** existen candidatos en varias etapas  
**Cuando** el Reclutador selecciona el filtro “Entrevista”  
**Entonces** la lista muestra únicamente los candidatos en esa etapa  

### Escenario: Ordenamiento por fecha de aplicación  
**Dado que** hay candidatos con fechas distintas  
**Cuando** el Reclutador ordena por “Fecha de aplicación” descendente  
**Entonces** el sistema muestra primero al más reciente  

---

## 5. Detalles Adicionales (Opcionales)  
**Prioridad:** `Alta`  
**Dependencias:** `ATS-US-04`  
**Notas Técnicas:** `—`  
**Diseño:** `Tabla-Candidatos-v1`  
**Métricas:** `Tiempo de carga < 1 s para 500 registros`  

---

## 6. Validación  
- [ ] Formato correcto  
- [ ] Criterios cubren filtrado y ordenamiento  
- [ ] Lenguaje claro  

---

---

## 1. Identificador Único  
`ATS-US-06`  

---

## 2. Título  
`Mover candidato entre etapas (Kanban)`  

---

## 3. Descripción  
*Como **Reclutador**, quiero **arrastrar a un candidato de una etapa a otra en un tablero Kanban** para **reflejar su avance de manera visual y rápida**.*  

---

## 4. Criterios de Aceptación  
### Escenario: Movimiento exitoso  
**Dado que** el Reclutador está en vista Kanban de una vacante  
**Cuando** arrastra la tarjeta del candidato de “Aplicado” a “Entrevista”  
**Entonces** el candidato cambia de etapa  
**Y** se registra un evento en la bitácora  

### Escenario: Etapa no permitida  
**Dado que** una etapa “Contratado” solo acepta 1 candidato  
**Cuando** el Reclutador intenta mover un segundo candidato a esa etapa  
**Entonces** el sistema muestra mensaje “Límite alcanzado”  
**Y** impide el movimiento  

---

## 5. Detalles Adicionales (Opcionales)  
**Prioridad:** `Alta`  
**Dependencias:** `ATS-US-05`, `ATS-US-01`  
**Notas Técnicas:** `Drag & drop Vue.js`  
**Diseño:** `Mockup-Kanban-v1`  
**Métricas:** `Acción de drag & drop < 200 ms`  

---

## 6. Validación  
- [ ] Formato correcto  
- [ ] Criterios cubren éxito y restricción  
- [ ] Redacción clara  

---

---

## 1. Identificador Único  
`ATS-US-07`  

---

## 2. Título  
`Envío automático de confirmación al candidato`  

---

## 3. Descripción  
*Como **Candidato**, quiero **recibir un correo de confirmación al aplicar** para **saber que mi solicitud fue recibida y está en proceso**.*  

---

## 4. Criterios de Aceptación  
### Escenario: Confirmación exitosa  
**Dado que** el sistema registra una nueva aplicación (ATS-US-04)  
**Cuando** el evento de “Nuevo candidato” se dispara  
**Entonces** el ATS envía un correo con asunto “Hemos recibido tu solicitud”  
**Y** el envío queda registrado en el historial de comunicaciones del candidato  

---

## 5. Detalles Adicionales (Opcionales)  
**Prioridad:** `Alta`  
**Dependencias:** `ATS-US-04`  
**Notas Técnicas:** `Plantilla HTML + SendGrid`  
**Diseño:** `Plantilla-Correo-Confirmacion`  
**Métricas:** `Tasa de entrega ≥ 98 %`  

---

## 6. Validación  
- [ ] Formato correcto  
- [ ] Criterio cubre notificación  
- [ ] Claro para no técnicos  

---

---

## 1. Identificador Único  
`ATS-US-08`  

---

## 2. Título  
`Gestión de roles y permisos`  

---

## 3. Descripción  
*Como **Administrador**, quiero **asignar roles (Admin, Recruiter, Hiring Manager) con permisos específicos** para **controlar el acceso a la información y acciones del ATS**.*  

---

## 4. Criterios de Aceptación  
### Escenario: Crear usuario Recruiter  
**Dado que** el Administrador crea un nuevo usuario  
**Cuando** selecciona el rol “Recruiter”  
**Entonces** el usuario puede acceder a crear vacantes y gestionar candidatos  
**Y** no puede modificar configuraciones globales  

### Escenario: Restricción de Hiring Manager  
**Dado que** un usuario tiene rol “Hiring Manager”  
**Cuando** intenta mover candidatos en el Kanban  
**Entonces** el sistema bloquea la acción  
**Y** muestra “Permiso denegado”  

---

## 5. Detalles Adicionales (Opcionales)  
**Prioridad:** `Alta`  
**Dependencias:** `—`  
**Notas Técnicas:** `RBAC en base de datos`  
**Diseño:** `—`  
**Métricas:** `Intentos de acceso no autorizado = 0`  

---

## 6. Validación  
- [ ] Formato correcto  
- [ ] Criterios cubren creación y restricción  
- [ ] Redacción clara  

---

---

## 1. Identificador Único  
`ATS-US-09`  

---

## 2. Título  
`Dashboard de métricas de reclutamiento`  

---

## 3. Descripción  
*Como **Hiring Manager**, quiero **ver un dashboard con indicadores clave (time-to-hire, embudo, origen de candidatos)** para **tomar decisiones basadas en datos**.*  

---

## 4. Criterios de Aceptación  
### Escenario: Visualizar time-to-hire promedio  
**Dado que** existen vacantes con candidatos contratados  
**Cuando** el Hiring Manager abre el dashboard  
**Entonces** se muestra el valor promedio de *time-to-hire* del período seleccionado  

### Escenario: Filtrar por vacante  
**Dado que** el dashboard está visible  
**Cuando** el Hiring Manager selecciona una vacante específica  
**Entonces** los gráficos se actualizan mostrando solo datos de esa vacante  

---

## 5. Detalles Adicionales (Opcionales)  
**Prioridad:** `Media`  
**Dependencias:** `ATS-US-05`, `ATS-US-06`  
**Notas Técnicas:** `Gráficos con biblioteca Chart.js`  
**Diseño:** `Wireframe-Dashboard-v1`  
**Métricas:** `Carga inicial < 2 s`  

---

## 6. Validación  
- [ ] Formato correcto  
- [ ] Criterios cubren visión global y filtro  
- [ ] Comprensible para no técnicos  

---

---

## 1. Identificador Único  
`ATS-US-10`  

---

## 2. Título  
`Sincronizar entrevistas con calendario`  

---

## 3. Descripción  
*Como **Reclutador**, quiero **programar entrevistas y sincronizarlas con Google Calendar/Outlook** para **evitar conflictos de agenda y enviar invitaciones automáticas**.*  

---

## 4. Criterios de Aceptación  
### Escenario: Crear evento en Google Calendar  
**Dado que** el Reclutador selecciona fecha y hora para entrevista  
**Cuando** confirma la programación  
**Entonces** el ATS crea un evento en Google Calendar con título “Entrevista – [Nombre Candidato]”  
**Y** envía invitación al entrevistador y candidato  

### Escenario: Actualizar horario  
**Dado que** existe un evento sincronizado  
**Cuando** el Reclutador cambia la hora en el ATS  
**Entonces** la invitación se actualiza en ambos calendarios  
**Y** se notifica a los involucrados  

---

## 5. Detalles Adicionales (Opcionales)  
**Prioridad:** `Media`  
**Dependencias:** `ATS-US-04`, `ATS-US-08`  
**Notas Técnicas:** `API Google Calendar v3 / Microsoft Graph`  
**Diseño:** `Flujo-Programar-Entrevista-v1`  
**Métricas:** `Tasa de sincronización exitosa ≥ 95 %`  

---

## 6. Validación  
- [ ] Formato correcto  
- [ ] Criterios cubren creación y actualización  
- [ ] Redacción clara  

---

# Backlog (priorizado con MoSCoW) – MVP ATS

1. **ATS-US-01 – Configurar etapas del flujo de reclutamiento** – **Must have**
2. **ATS-US-02 – Crear vacante** – **Must have**
3. **ATS-US-03 – Publicar vacante en portal externo** – **Must have**
4. **ATS-US-04 – Recepción automática de candidatos** – **Must have**
5. **ATS-US-05 – Visualizar listado de candidatos centralizado** – **Must have**
6. **ATS-US-06 – Mover candidato entre etapas (Kanban)** – **Must have**
7. **ATS-US-07 – Envío automático de confirmación al candidato** – **Must have**
8. **ATS-US-08 – Gestión de roles y permisos** – **Must have**
9. **ATS-US-09 – Dashboard de métricas de reclutamiento** – **Should have**
10. **ATS-US-10 – Sincronizar entrevistas con calendario** – **Could have**

# Matriz de Priorización **Value vs. Effort** – Backlog MVP ATS

|                      | **Bajo Esfuerzo** | **Alto Esfuerzo** |
|----------------------|-------------------|-------------------|
| **Alto Valor** | **Quick Wins**  <br>- **ATS-US-01** – Configurar etapas del flujo de reclutamiento – *Quick Win*  <br>- **ATS-US-02** – Crear vacante – *Quick Win*  <br>- **ATS-US-05** – Visualizar listado de candidatos centralizado – *Quick Win*  <br>- **ATS-US-06** – Mover candidato entre etapas (Kanban) – *Quick Win*  <br>- **ATS-US-07** – Envío automático de confirmación al candidato – *Quick Win* | **Big Bets**  <br>- **ATS-US-03** – Publicar vacante en portal externo – *Big Bet*  <br>- **ATS-US-04** – Recepción automática de candidatos – *Big Bet*  <br>- **ATS-US-08** – Gestión de roles y permisos – *Big Bet* |
| **Bajo Valor** | **Fill-Ins**  <br>- **ATS-US-09** – Dashboard de métricas de reclutamiento – *Fill-In* | **Time Sinks**  <br>- **ATS-US-10** – Sincronizar entrevistas con calendario – *Time Sink* |

# Backlog detallado – Historia de Usuario **ATS-US-01**  
> *Configurar etapas del flujo de reclutamiento*  

---

## Categoría 1: Investigación
### Ticket 1

## Título
`Benchmark de flujos de reclutamiento en ATS líderes`

## Descripción
Analizar cómo los principales ATS (Greenhouse, Lever, Workable) permiten crear, ordenar y gestionar etapas, identificando mejores prácticas, patrones de UX y limitaciones.

## Criterios de Aceptación
- Se entrega un reporte comparativo con al menos 3 herramientas.
- Se destacan pros/contras y recomendaciones aplicables al proyecto.
- El reporte se comparte con UX y Producto en la wiki del equipo.

## Prioridad
`Media`

## Asignado a
`Product Research Team`

## Etiquetas
`Investigación`, `Producto`, `Sprint-1`

## Comentarios
Incluir capturas de pantalla y flujos resumidos para referencia rápida.

## Enlaces
[Documento de benchmarking](#), [Greenhouse docs](#)

## Historial de Cambios
- `2025-06-09`: Creación del ticket por PM  

---

### Ticket 2


## Título
`Análisis técnico del modelo de datos para etapas`

## Descripción
Revisar la base de datos actual y definir cómo introducir una nueva tabla “stages” y su relación con “vacancies” sin romper integridad de datos.

## Criterios de Aceptación
- Documento ER actualizado con la tabla y campos propuestos.
- Lista de migraciones necesarias y retrocompatibilidad definida.
- Validación de impacto en consultas existentes.

## Prioridad
`Alta`

## Asignado a
`Backend Team`

## Etiquetas
`Investigación`, `DB`, `Sprint-1`

## Comentarios
Tomar en cuenta que el sistema no está orientado a microservicios.

## Enlaces
[Esquema actual DB](#)

## Historial de Cambios
- `2025-06-09`: Creación del ticket por PM  

---

### Ticket 3


## Título
`Definir estrategia QA para módulo de etapas`

## Descripción
Determinar el alcance de pruebas (unitarias, integración, e2e) y herramientas (Jest, Cypress) necesarias para garantizar calidad del nuevo módulo.

## Criterios de Aceptación
- Documento de estrategia QA revisado por QA Lead.
- Matriz de riesgos y cobertura mínima acordada.
- Plan de casos de prueba iniciales esbozado.

## Prioridad
`Media`

## Asignado a
`QA Team`

## Etiquetas
`Investigación`, `QA`, `Sprint-1`

## Comentarios
Coordinarse con Backend y Frontend para alinear métricas de cobertura.

## Enlaces
[Plantilla estrategia QA](#)

## Historial de Cambios
- `2025-06-09`: Creación del ticket por PM  

---

## Categoría 2: Features / Características
### Ticket 4


## Título
`Definir Design System mínimo viable (MVP)`

## Descripción
Crear lineamientos básicos de UI (tipografías, paleta de colores, espaciado, componentes comunes) para asegurar consistencia en todo el ATS empezando por el módulo de etapas.

## Criterios de Aceptación
- Guía visual documentada (Figma) con tokens de diseño.
- Componente base de botón, modal y tabla definidos.
- Validación de accesibilidad (contraste AA).

## Prioridad
`Alta`

## Asignado a
`UX/UI Team`

## Etiquetas
`Feature`, `Design System`, `Sprint-1`

## Comentarios
Partimos desde cero; seguir principios de atomic design.

## Enlaces
[Figma Design System draft](#)

## Historial de Cambios
- `2025-06-09`: Creación del ticket por PM  

---

### Ticket 5


## Título
`Diseñar experiencia de usuario para Configuración de Etapas`

## Descripción
Prototipar el flujo completo (lista, crear, editar, eliminar, reordenar) considerando drag-and-drop y validaciones inline.

## Criterios de Aceptación
- Prototipo de alta fidelidad en Figma revisado con stakeholders.
- Incluye estados vacíos, errores y confirmaciones.
- Aprobación del Product Owner.

## Prioridad
`Alta`

## Asignado a
`UX/UI Team`

## Etiquetas
`Feature`, `UX`, `Sprint-2`

## Comentarios
Utilizar componentes del Design System (Ticket 4).

## Enlaces
[Figma Prototype](#)

## Historial de Cambios
- `2025-06-09`: Creación del ticket por PM  

---

### Ticket 6


## Título
`Componente Vue para gestión de etapas`

## Descripción
Implementar en Vue 3 un componente que consuma la API y permita:  
1) listar etapas,  
2) crear/editar mediante modal,  
3) reordenar con drag-and-drop,  
4) eliminar con confirmación.

## Criterios de Aceptación
- Funcionalidad completa en entorno de staging.
- Cumple guidelines del Design System.
- Cobertura de pruebas unitarias ≥ 80 %.

## Prioridad
`Crítica`

## Asignado a
`Frontend Team`

## Etiquetas
`Feature`, `Frontend`, `Sprint-3`

## Comentarios
Incluir accesibilidad (teclado) para drag-and-drop.

## Enlaces
[API Spec Etapas](#)

## Historial de Cambios
- `2025-06-09`: Creación del ticket por PM  

---

## Categoría 3: Tareas Técnicas
### Ticket 7


## Título
`API REST CRUD de Etapas`

## Descripción
Crear endpoints `/stages` (GET, POST, PUT, DELETE, PATCH reorder) con validaciones y control de errores.

## Criterios de Aceptación
- Endpoints documentados en Swagger.
- Tests unitarios y de integración (coverage ≥ 85 %).
- Autenticación y autorización vía JWT y RBAC.

## Prioridad
`Crítica`

## Asignado a
`Backend Team`

## Etiquetas
`Technical`, `Backend`, `Sprint-2`

## Comentarios
Seguir convenciones REST ya existentes.

## Enlaces
[Guía de APIs internas](#)

## Historial de Cambios
- `2025-06-09`: Creación del ticket por PM  

---

### Ticket 8


## Título
`Migración BD: tabla stages y relaciones`

## Descripción
Crear script de migración para la tabla `stages` (id, name, position, vacancy_id nullable) y actualizar `vacancies` para referencia.

## Criterios de Aceptación
- Migración reversible sin pérdida de datos.
- Índices para búsquedas por vacancy_id.
- Validado en ambiente de staging.

## Prioridad
`Alta`

## Asignado a
`Backend Team`

## Etiquetas
`Technical`, `DB`, `Sprint-2`

## Comentarios
Usar herramienta de migraciones actual (Knex).

## Enlaces
[Modelo ER propuesto](#)

## Historial de Cambios
- `2025-06-09`: Creación del ticket por PM  

---

### Ticket 9


## Título
`Propagación de cambios de etapas a vacantes`

## Descripción
Asegurarse de que al renombrar/eliminar etapas se actualicen las vacantes y candidatos relacionados sin inconsistencias.

## Criterios de Aceptación
- Al renombrar, todos los registros históricos conservan trazabilidad.
- Al eliminar, se bloquea si hay candidatos activos; si no, se purga sin errores.
- Casos de prueba en integración.

## Prioridad
`Alta`

## Asignado a
`Backend Team`

## Etiquetas
`Technical`, `Data Integrity`, `Sprint-3`

## Comentarios
Requiere coordinación con Frontend para mensajes de error.

## Enlaces
[Documento de reglas de negocio](#)

## Historial de Cambios
- `2025-06-09`: Creación del ticket por PM  

---

### Ticket 10


## Título
`Control de permisos para Configuración de Etapas`

## Descripción
Aplicar RBAC de modo que solo usuarios con rol Admin puedan crear/editar/eliminar etapas; Recruiter y Hiring Manager solo lectura.

## Criterios de Aceptación
- Middleware verifica rol antes de acceder al endpoint.
- Pruebas de seguridad que prueben intento no autorizado.
- Auditoría de intentos fallidos registrada.

## Prioridad
`Alta`

## Asignado a
`Backend Team`

## Etiquetas
`Technical`, `Security`, `Sprint-3`

## Comentarios
Reutilizar librería de permisos existente.

## Enlaces
[Documento de roles](#)

## Historial de Cambios
- `2025-06-09`: Creación del ticket por PM  

---

### Ticket 11


## Título
`Pruebas E2E Configuración de Etapas`

## Descripción
Crear suite de pruebas end-to-end con Cypress que cubra los escenarios de creación, edición, eliminación y reordenamiento.

## Criterios de Aceptación
- Suite ejecuta en CI con tiempo ≤ 3 min.
- Todas las pruebas pasan en master.
- Reporte de resultados accesible en Dashboard QA.

## Prioridad
`Media`

## Asignado a
`QA Team`

## Etiquetas
`Technical`, `QA`, `Sprint-4`

## Comentarios
Coordinar con Frontend para fixtures.

## Enlaces
[Guía Cypress](#)

## Historial de Cambios
- `2025-06-09`: Creación del ticket por PM  

---

### Ticket 12


## Título
`Documentación de usuario y administrador`

## Descripción
Redactar manuales y ayudas contextuales sobre cómo configurar etapas, incluyendo FAQ y mejores prácticas.

## Criterios de Aceptación
- Manual PDF y página en la wiki publicados.
- Incluye capturas del sistema y video corto de 2 min.
- Revisado por Product Owner y UX.

## Prioridad
`Media`

## Asignado a
`Tech Writing Team`

## Etiquetas
`Technical`, `Docs`, `Sprint-4`

## Comentarios
Actualizar enlaces en la app hacia esta guía.

## Enlaces
[Plantilla de documentación](#)

## Historial de Cambios
- `2025-06-09`: Creación del ticket por PM  

---

## Categoría 4: Posibles Mejoras
### Ticket 13


## Título
`Importar y exportar plantillas de flujo`

## Descripción
Permitir a los usuarios exportar su flujo de etapas en JSON y volverlo a importar o compartir con otras cuentas.

## Criterios de Aceptación
- Botón “Exportar” descarga JSON válido.
- Botón “Importar” valida formato y crea flujo nuevo.
- Manejo de errores de formato incorrecto.

## Prioridad
`Baja`

## Asignado a
`Frontend Team`

## Etiquetas
`Mejora`, `Frontend`, `Sprint-Backlog`

## Comentarios
Se desarrolla después del MVP, sujeto a capacidad.

## Enlaces
[Spec JSON](#)

## Historial de Cambios
- `2025-06-09`: Creación del ticket por PM  

---

### Ticket 14


## Título
`Versionado y auditoría de flujos de etapas`

## Descripción
Guardar historial de cambios en flujos para poder restaurar versiones anteriores y mostrar auditoría.

## Criterios de Aceptación
- Cada cambio registra usuario, fecha y tipo de acción.
- Interfaz de “Revertir a versión” disponible para Admin.
- Logs accesibles solo para Admin.

## Prioridad
`Baja`

## Asignado a
`Backend Team`

## Etiquetas
`Mejora`, `Audit`, `Sprint-Backlog`

## Comentarios
Depende de Tickets 7-10; planificar para después del MVP.

## Enlaces
[Propuesta de auditoría](#)

## Historial de Cambios
- `2025-06-09`: Creación del ticket por PM  

# Estimación de Esfuerzo – T-Shirt Sizing  
*Módulo: ATS-US-01 – Configurar etapas del flujo de reclutamiento*

| Nº Ticket | Título                                                       | Talla | Equivalencia (horas) |
|-----------|--------------------------------------------------------------|-------|----------------------|
| 1         | Benchmark de flujos de reclutamiento en ATS líderes          | S     | 8 h |
| 2         | Análisis técnico del modelo de datos para etapas             | M     | 16 h |
| 3         | Definir estrategia QA para módulo de etapas                  | S     | 8 h |
| 4         | Definir Design System mínimo viable (MVP)                    | L     | 32 h |
| 5         | Diseñar experiencia de usuario para Configuración de Etapas  | M     | 16 h |
| 6         | Componente Vue para gestión de etapas                        | L     | 32 h |
| 7         | API REST CRUD de Etapas                                      | L     | 32 h |
| 8         | Migración BD: tabla stages y relaciones                      | M     | 16 h |
| 9         | Propagación de cambios de etapas a vacantes                  | M     | 16 h |
| 10        | Control de permisos para Configuración de Etapas             | M     | 16 h |
| 11        | Pruebas E2E Configuración de Etapas                          | M     | 16 h |
| 12        | Documentación de usuario y administrador                     | S     | 8 h |
| 13        | Importar y exportar plantillas de flujo                      | M     | 16 h |
| 14        | Versionado y auditoría de flujos de etapas                   | L     | 32 h |

