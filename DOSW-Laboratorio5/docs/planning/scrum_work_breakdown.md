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
| **ID** | DLC-1 |
| **Título** | Gestión de Cuentas Bancarias |
| **Descripción** | Bankify necesita un módulo centralizado que permita crear, activar, inactivar y actualizar cuentas bancarias con validaciones de negocio específicas (número de 10 dígitos, banco registrado, etc.), garantizando que los asesores y clientes puedan administrar las cuentas de forma segura y controlada. Sin este módulo, no es posible operar el sistema financiero básico que requiere la startup para validar su modelo de negocio. |
| **Stakeholder** | Gerente de Operaciones de Bankify / Asesores / Clientes |

---

## 2. Historias de Usuario

### HU-01 – Crear cuenta bancaria

| Campo | Descripción |
|-------|-------------|
| **ID** | DLC-2 |
| **Título** | Crear cuenta bancaria validada |
| **Descripción** | Como **asesor** quiero poder crear una cuenta bancaria para un cliente, ingresando el número de cuenta de 10 dígitos y el banco asociado, para garantizar que la cuenta cumple las reglas de negocio antes de ser registrada en el sistema. |
| **Prioridad** | **Alta** |
| **Justificación de prioridad** | Es el punto de entrada del sistema. Sin la capacidad de crear cuentas no es posible ejecutar ninguna otra funcionalidad (consulta de saldo, depósitos, reportes). Bloquea a todas las demás historias de usuario. |
| **Estimación** | _Puntos de historia_ |

---

### HU-02 – Activar / Inactivar cuenta bancaria

| Campo | Descripción |
|-------|-------------|
| **ID** | DLC-3 |
| **Título** | Activar e inactivar cuenta bancaria |
| **Descripción** | Como **asesor o cliente** quiero poder activar o inactivar una cuenta bancaria existente para controlar si dicha cuenta puede ser usada en operaciones financieras (depósitos, consultas), protegiendo al cliente de movimientos no autorizados. |
| **Prioridad** | **Alta** |
| **Justificación de prioridad** | El ciclo de vida de una cuenta (activa/inactiva) es un requisito de negocio básico señalado explícitamente por el gerente de operaciones. Sin este control, las cuentas no podrían ser bloqueadas ante situaciones de riesgo. |
| **Estimación** | _Puntos de historia_ |

---

### HU-03 – Consultar saldo de cuenta

| Campo | Descripción |
|-------|-------------|
| **ID** | DLC-4 |
| **Título** | Consultar saldo de cuenta bancaria |
| **Descripción** | Como **cliente** quiero poder consultar el saldo actual de mi cuenta bancaria para conocer en tiempo real el dinero disponible y tomar decisiones financieras informadas. |
| **Prioridad** | **Alta** |
| **Justificación de prioridad** | Es una funcionalidad esencial de cualquier sistema bancario y uno de los requerimientos explícitos de Bankify para la primera versión del producto. Los clientes la usarán con alta frecuencia. |
| **Estimación** | _Puntos de historia_ |

---

### HU-04 – Actualizar información de cuenta bancaria

| Campo | Descripción |
|-------|-------------|
| **ID** | DLC-5 |
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
| **ID** | DLC-6 |
| **Título** | Implementar validación del número de cuenta |
| **ID Historia asociada** | DLC-2 |
| **Descripción** | Como **desarrollador** quiero implementar la lógica de validación que verifique que el número de cuenta tenga exactamente 10 dígitos, contenga solo números y no incluya caracteres especiales, para garantizar la integridad del dato desde el ingreso. |
| **Tareas requisito** | — |

| Campo | Descripción |
|-------|-------------|
| **ID** | DLC-7 |
| **Título** | Implementar validación del banco asociado |
| **ID Historia asociada** | DLC-2 |
| **Descripción** | Como **desarrollador** quiero implementar la validación que verifique que los dos primeros dígitos del número de cuenta correspondan a un banco registrado en el sistema (e.g., 01 → Bancolombia, 02 → Davivienda), para rechazar cuentas con bancos no reconocidos. |
| **Tareas requisito** | DLC-6 |

| Campo | Descripción |
|-------|-------------|
| **ID** | DLC-8 |
| **Título** | Crear endpoint REST para registro de cuenta |
| **ID Historia asociada** | DLC-2 |
| **Descripción** | Como **desarrollador** quiero exponer un endpoint REST (POST /cuentas) que reciba los datos de la cuenta, ejecute las validaciones y persista la cuenta en la base de datos si es válida, retornando el identificador asignado. |
| **Tareas requisito** | DLC-6, DLC-7 |

---

### Tareas de HU-02 – Activar e inactivar cuenta bancaria

| Campo | Descripción |
|-------|-------------|
| **ID** | DLC-9 |
| **Título** | Implementar lógica de cambio de estado de cuenta |
| **ID Historia asociada** | DLC-3 |
| **Descripción** | Como **desarrollador** quiero implementar el servicio que permita cambiar el estado de una cuenta entre ACTIVA e INACTIVA, validando que la cuenta exista en el sistema antes de realizar el cambio. |
| **Tareas requisito** | DLC-8 |

| Campo | Descripción |
|-------|-------------|
| **ID** | DLC-10 |
| **Título** | Controlar permisos por rol para activar/inactivar |
| **ID Historia asociada** | DLC-3 |
| **Descripción** | Como **desarrollador** quiero implementar la lógica de autorización para que los clientes solo puedan inactivar su propia cuenta, y los asesores puedan activar o inactivar cualquier cuenta, para respetar las reglas de roles definidas por Bankify. |
| **Tareas requisito** | DLC-9 |

| Campo | Descripción |
|-------|-------------|
| **ID** | DLC-11 |
| **Título** | Crear endpoint REST para cambio de estado de cuenta |
| **ID Historia asociada** | DLC-3 |
| **Descripción** | Como **desarrollador** quiero exponer un endpoint REST (PATCH /cuentas/{id}/estado) que reciba el nuevo estado deseado y aplique el cambio si el usuario tiene el rol autorizado, retornando confirmación de la operación. |
| **Tareas requisito** | DLC-9, DLC-10 |

---

### Tareas de HU-03 – Consultar saldo de cuenta bancaria

| Campo | Descripción |
|-------|-------------|
| **ID** | DLC-12 |
| **Título** | Implementar servicio de consulta de saldo |
| **ID Historia asociada** | DLC-4 |
| **Descripción** | Como **desarrollador** quiero implementar el servicio que recupere el saldo actual de una cuenta dado su número, verificando que la cuenta exista y esté activa antes de retornar la información. |
| **Tareas requisito** | DLC-8 |

| Campo | Descripción |
|-------|-------------|
| **ID** | DLC-13 |
| **Título** | Controlar acceso a la consulta por propietario |
| **ID Historia asociada** | DLC-4 |
| **Descripción** | Como **desarrollador** quiero implementar la validación de que solo el cliente propietario de la cuenta pueda consultar su saldo, para proteger la información financiera del usuario. |
| **Tareas requisito** | DLC-12 |

| Campo | Descripción |
|-------|-------------|
| **ID** | DLC-14 |
| **Título** | Crear endpoint REST para consulta de saldo |
| **ID Historia asociada** | DLC-4 |
| **Descripción** | Como **desarrollador** quiero exponer un endpoint REST (GET /cuentas/{id}/saldo) que retorne el saldo actual de la cuenta autenticada, con los datos formateados y el mensaje de respuesta adecuado. |
| **Tareas requisito** | DLC-12, DLC-13 |

---

### Tareas de HU-04 – Actualizar información de cuenta bancaria

| Campo | Descripción |
|-------|-------------|
| **ID** | DLC-15 |
| **Título** | Definir campos actualizables de la cuenta |
| **ID Historia asociada** | DLC-5 |
| **Descripción** | Como **desarrollador** quiero definir y documentar qué campos de la cuenta pueden ser modificados (excluyendo el número de cuenta y el banco), para garantizar que las actualizaciones no comprometan las reglas de negocio del sistema. |
| **Tareas requisito** | DLC-8 |

| Campo | Descripción |
|-------|-------------|
| **ID** | DLC-16 |
| **Título** | Implementar servicio de actualización de cuenta |
| **ID Historia asociada** | DLC-5 |
| **Descripción** | Como **desarrollador** quiero implementar el servicio que permita actualizar los campos permitidos de una cuenta bancaria, validando que la cuenta exista y que el usuario tenga el rol de asesor para ejecutar la operación. |
| **Tareas requisito** | DLC-15 |

| Campo | Descripción |
|-------|-------------|
| **ID** | DLC-17 |
| **Título** | Crear endpoint REST para actualización de cuenta |
| **ID Historia asociada** | DLC-5 |
| **Descripción** | Como **desarrollador** quiero exponer un endpoint REST (PUT /cuentas/{id}) que reciba los campos a actualizar, aplique las validaciones necesarias y persista los cambios en la base de datos, retornando la cuenta actualizada. |
| **Tareas requisito** | DLC-15, DLC-16 |

---
