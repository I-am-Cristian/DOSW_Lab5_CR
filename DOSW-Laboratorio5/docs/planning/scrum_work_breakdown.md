# Scrum Work Breakdown – Bankify
---

## Roles del Equipo Scrum

| Rol | Integrante |
|-----|------------|
| Product Owner | Cristian Gonzalez |
| Scrum Master | Rafael Moreno |
| Desarrollador | Ambos |

---

## 1. Épica

| Campo | Descripción |
|-------|-------------|
| **ID** | EP-01 |
| **Título** | Gestión de Cuentas Bancarias |
| **Descripción** | Bankify necesita un módulo centralizado que permita crear, activar, inactivar y actualizar cuentas bancarias con validaciones de negocio específicas (número de 10 dígitos, banco registrado, etc.), garantizando que los asesores y clientes puedan administrar las cuentas de forma segura y controlada. Sin este módulo, no es posible operar el sistema financiero básico que requiere la startup para validar su modelo de negocio. |
| **Stakeholder** | Gerente de Operaciones de Bankify / Asesores / Clientes |

---

## 2. Historias de Usuario

### HU-01 – Crear cuenta bancaria

| Campo | Descripción |
|-------|-------------|
| **ID** | HU-01 |
| **Título** | Crear cuenta bancaria validada |
| **Descripción** | Como **asesor** quiero poder crear una cuenta bancaria para un cliente, ingresando el número de cuenta de 10 dígitos y el banco asociado, para garantizar que la cuenta cumple las reglas de negocio antes de ser registrada en el sistema. |
| **Prioridad** | **Alta** |
| **Justificación de prioridad** | Es el punto de entrada del sistema. Sin la capacidad de crear cuentas no es posible ejecutar ninguna otra funcionalidad (consulta de saldo, depósitos, reportes). Bloquea a todas las demás historias de usuario. |
| **Estimación** | _Puntos de historia_ |

---

### HU-02 – Activar / Inactivar cuenta bancaria

| Campo | Descripción |
|-------|-------------|
| **ID** | HU-02 |
| **Título** | Activar e inactivar cuenta bancaria |
| **Descripción** | Como **asesor o cliente** quiero poder activar o inactivar una cuenta bancaria existente para controlar si dicha cuenta puede ser usada en operaciones financieras (depósitos, consultas), protegiendo al cliente de movimientos no autorizados. |
| **Prioridad** | **Alta** |
| **Justificación de prioridad** | El ciclo de vida de una cuenta (activa/inactiva) es un requisito de negocio básico señalado explícitamente por el gerente de operaciones. Sin este control, las cuentas no podrían ser bloqueadas ante situaciones de riesgo. |
| **Estimación** | _Puntos de historia_ |

---

### HU-03 – Consultar saldo de cuenta

| Campo | Descripción |
|-------|-------------|
| **ID** | HU-03 |
| **Título** | Consultar saldo de cuenta bancaria |
| **Descripción** | Como **cliente** quiero poder consultar el saldo actual de mi cuenta bancaria para conocer en tiempo real el dinero disponible y tomar decisiones financieras informadas. |
| **Prioridad** | **Alta** |
| **Justificación de prioridad** | Es una funcionalidad esencial de cualquier sistema bancario y uno de los requerimientos explícitos de Bankify para la primera versión del producto. Los clientes la usarán con alta frecuencia. |
| **Estimación** | _Puntos de historia_ |

---

### HU-04 – Actualizar información de cuenta bancaria

| Campo | Descripción |
|-------|-------------|
| **ID** | HU-04 |
| **Título** | Actualizar información de cuenta bancaria |
| **Descripción** | Como **asesor** quiero poder actualizar los datos de una cuenta bancaria existente (por ejemplo, tipo de cuenta o información adicional) para mantener la información del cliente actualizada y correcta dentro del sistema. |
| **Prioridad** | **Media** |
| **Justificación de prioridad** | Aunque es necesaria para la operación completa del módulo, no bloquea las funcionalidades principales (crear, consultar, activar/inactivar). Puede desarrollarse en un sprint posterior una vez las historias de alta prioridad estén implementadas. |
| **Estimación** | _Puntos de historia_ |

---

## 3. Tareas

### Tareas de HU-01 – Crear cuenta bancaria validada

| Campo | Descripción |
|-------|-------------|
| **ID** | TR-01 |
| **Título** | Implementar validación del número de cuenta |
| **ID Historia asociada** | HU-01 |
| **Descripción** | Como **desarrollador** quiero implementar la lógica de validación que verifique que el número de cuenta tenga exactamente 10 dígitos, contenga solo números y no incluya caracteres especiales, para garantizar la integridad del dato desde el ingreso. |
| **Tareas requisito** | — |

| Campo | Descripción |
|-------|-------------|
| **ID** | TR-02 |
| **Título** | Implementar validación del banco asociado |
| **ID Historia asociada** | HU-01 |
| **Descripción** | Como **desarrollador** quiero implementar la validación que verifique que los dos primeros dígitos del número de cuenta correspondan a un banco registrado en el sistema (e.g., 01 → Bancolombia, 02 → Davivienda), para rechazar cuentas con bancos no reconocidos. |
| **Tareas requisito** | TR-01 |

| Campo | Descripción |
|-------|-------------|
| **ID** | TR-03 |
| **Título** | Crear endpoint REST para registro de cuenta |
| **ID Historia asociada** | HU-01 |
| **Descripción** | Como **desarrollador** quiero exponer un endpoint REST (POST /cuentas) que reciba los datos de la cuenta, ejecute las validaciones y persista la cuenta en la base de datos si es válida, retornando el identificador asignado. |
| **Tareas requisito** | TR-01, TR-02 |

---

### Tareas de HU-02 – Activar e inactivar cuenta bancaria

| Campo | Descripción |
|-------|-------------|
| **ID** | TR-04 |
| **Título** | Implementar lógica de cambio de estado de cuenta |
| **ID Historia asociada** | HU-02 |
| **Descripción** | Como **desarrollador** quiero implementar el servicio que permita cambiar el estado de una cuenta entre ACTIVA e INACTIVA, validando que la cuenta exista en el sistema antes de realizar el cambio. |
| **Tareas requisito** | TR-03 |

| Campo | Descripción |
|-------|-------------|
| **ID** | TR-05 |
| **Título** | Controlar permisos por rol para activar/inactivar |
| **ID Historia asociada** | HU-02 |
| **Descripción** | Como **desarrollador** quiero implementar la lógica de autorización para que los clientes solo puedan inactivar su propia cuenta, y los asesores puedan activar o inactivar cualquier cuenta, para respetar las reglas de roles definidas por Bankify. |
| **Tareas requisito** | TR-04 |

| Campo | Descripción |
|-------|-------------|
| **ID** | TR-06 |
| **Título** | Crear endpoint REST para cambio de estado de cuenta |
| **ID Historia asociada** | HU-02 |
| **Descripción** | Como **desarrollador** quiero exponer un endpoint REST (PATCH /cuentas/{id}/estado) que reciba el nuevo estado deseado y aplique el cambio si el usuario tiene el rol autorizado, retornando confirmación de la operación. |
| **Tareas requisito** | TR-04, TR-05 |

---

### Tareas de HU-03 – Consultar saldo de cuenta bancaria

| Campo | Descripción |
|-------|-------------|
| **ID** | TR-07 |
| **Título** | Implementar servicio de consulta de saldo |
| **ID Historia asociada** | HU-03 |
| **Descripción** | Como **desarrollador** quiero implementar el servicio que recupere el saldo actual de una cuenta dado su número, verificando que la cuenta exista y esté activa antes de retornar la información. |
| **Tareas requisito** | TR-03 |

| Campo | Descripción |
|-------|-------------|
| **ID** | TR-08 |
| **Título** | Controlar acceso a la consulta por propietario |
| **ID Historia asociada** | HU-03 |
| **Descripción** | Como **desarrollador** quiero implementar la validación de que solo el cliente propietario de la cuenta pueda consultar su saldo, para proteger la información financiera del usuario. |
| **Tareas requisito** | TR-07 |

| Campo | Descripción |
|-------|-------------|
| **ID** | TR-09 |
| **Título** | Crear endpoint REST para consulta de saldo |
| **ID Historia asociada** | HU-03 |
| **Descripción** | Como **desarrollador** quiero exponer un endpoint REST (GET /cuentas/{id}/saldo) que retorne el saldo actual de la cuenta autenticada, con los datos formateados y el mensaje de respuesta adecuado. |
| **Tareas requisito** | TR-07, TR-08 |

---

### Tareas de HU-04 – Actualizar información de cuenta bancaria

| Campo | Descripción |
|-------|-------------|
| **ID** | TR-10 |
| **Título** | Definir campos actualizables de la cuenta |
| **ID Historia asociada** | HU-04 |
| **Descripción** | Como **desarrollador** quiero definir y documentar qué campos de la cuenta pueden ser modificados (excluyendo el número de cuenta y el banco), para garantizar que las actualizaciones no comprometan las reglas de negocio del sistema. |
| **Tareas requisito** | TR-03 |

| Campo | Descripción |
|-------|-------------|
| **ID** | TR-11 |
| **Título** | Implementar servicio de actualización de cuenta |
| **ID Historia asociada** | HU-04 |
| **Descripción** | Como **desarrollador** quiero implementar el servicio que permita actualizar los campos permitidos de una cuenta bancaria, validando que la cuenta exista y que el usuario tenga el rol de asesor para ejecutar la operación. |
| **Tareas requisito** | TR-10 |

| Campo | Descripción |
|-------|-------------|
| **ID** | TR-12 |
| **Título** | Crear endpoint REST para actualización de cuenta |
| **ID Historia asociada** | HU-04 |
| **Descripción** | Como **desarrollador** quiero exponer un endpoint REST (PUT /cuentas/{id}) que reciba los campos a actualizar, aplique las validaciones necesarias y persista los cambios en la base de datos, retornando la cuenta actualizada. |
| **Tareas requisito** | TR-10, TR-11 |

---

## 4. Video de estimación (Planning Poker)

> _Enlace al video de estimación de la historia de usuario seleccionada (a completar en la Parte 4)_

| Historia estimada en video | Enlace |
|---------------------------|--------|
| HU-01 – Crear cuenta bancaria validada | [Insertar enlace aquí] |

---

## 5. Resumen de estimaciones (Planning Poker)

| ID | Historia de Usuario | Prioridad | Puntos de Historia |
|----|--------------------|-----------|--------------------|
| HU-01 | Crear cuenta bancaria validada | Alta | _Por definir_ |
| HU-02 | Activar e inactivar cuenta bancaria | Alta | _Por definir_ |
| HU-03 | Consultar saldo de cuenta bancaria | Alta | _Por definir_ |
| HU-04 | Actualizar información de cuenta bancaria | Media | _Por definir_ |

---
